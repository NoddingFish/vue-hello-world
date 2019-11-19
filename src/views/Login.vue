<template>
  <el-container style="height: 100%;" direction="vertical">
    <el-main>
      <el-row>
        <el-col :span="24">
          <img src="https://cn.vuejs.org/images/logo.png" width="200px;" alt="">
        </el-col>
      </el-row>
      <el-form :model="ruleForm" ref="ruleForm" :rules="rules" label-width="80px" v-if="!ruleForm.isReg">
        <el-row>
          <el-col :span="24">
            <el-form-item prop="name" label-width="0px">
              <el-input v-model="ruleForm.name">
                <template slot="prepend">用户名</template>
              </el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-form-item prop="password" label-width="0px">
              <el-input v-model="ruleForm.password" show-password>
                <template slot="prepend">密码</template>
              </el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-button type="primary" plain @click="login('ruleForm')">登录</el-button>
            <el-button type="primary" plain @click="reg('ruleForm')">注册</el-button>
          </el-col>
        </el-row>
      </el-form>
      <el-form :model="ruleForm" ref="ruleForm" :rules="rules" label-width="80px" v-else>
        <el-row>
          <el-col :span="24">
            <el-form-item prop="name" label-width="0px">
              <el-input v-model="ruleForm.name">
                <template slot="prepend">用户名</template>
              </el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-form-item prop="password" label-width="0px">
              <el-input v-model="ruleForm.password" show-password>
                <template slot="prepend">密码</template>
              </el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-form-item prop="repeat" label-width="0px">
              <el-input v-model="ruleForm.repeat" show-password>
                <template slot="prepend">确认密码</template>
              </el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-button type="primary" plain @click="addUser('ruleForm')">确定</el-button>
            <el-button type="primary" plain @click="cancel('ruleForm')">取消</el-button>
          </el-col>
        </el-row>
      </el-form>
    </el-main>
  </el-container>
</template>

<script>
  export default {
    name: 'Login',
    data () {
      return {
        ruleForm: {
          isReg: false,
          name: '',
          password: '',
          repeat: ''
        },
        rules: {
          name: [
            { required: true, message: '昵称必填', trigger: 'change' }
          ],
          password: [
            { required: true, message: '密码必填', trigger: 'change' }
          ],
          repeat: [
            { required: true, message: '密码必填', trigger: 'change' }
          ]
        }
      }
    },
    methods: {
      login (formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            if (localStorage.getItem('name') === this.ruleForm.name && localStorage.getItem('password') === this.ruleForm.password) {
              this.ruleForm.name = ''
              this.ruleForm.password = ''
              this.$router.push('/home')
            } else {
              this.$message({
                showClose: true,
                type: 'error',
                message: '用户名或密码输入不正确'
              })
            }
          } else {
            return false
          }
        })
      },
      reg (formName) {
        this.ruleForm.isReg = true
        this.$refs[formName].resetFields()
      },
      addUser (formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            if (this.ruleForm.password === this.ruleForm.repeat) {
              localStorage.setItem('name', this.ruleForm.name)
              localStorage.setItem('password', this.ruleForm.password)
              this.ruleForm.name = ''
              this.ruleForm.password = ''
              this.ruleForm.isReg = false
            } else {
              alert('两次输入密码不一致')
            }
          } else {
            return false
          }
        })
      },
      cancel (formName) {
        this.ruleForm.isReg = false
        this.$refs[formName].resetFields()
      }
    }
  }
</script>

<style scoped>
  html, body, #app, .el-container {
    /*设置内部填充为0，几个布局元素之间没有间距*/
    padding: 0px;
    /*外部间距也是如此设置*/
    margin: 0px;
    /*统一设置高度为100%*/
    height: 100%;
  }
</style>

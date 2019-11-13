<template>
  <el-container style="height: 100%;" direction="vertical">
    <el-main>
      <el-row>
        <el-col :span="24">
          <img src="https://cn.vuejs.org/images/logo.png" width="200px;" alt="">
        </el-col>
      </el-row>
      <el-form ref="form" label-width="80px" v-if="!isReg">
        <el-row>
          <el-col :span="24">
            <el-form-item label="用户名">
              <el-input v-model="name"></el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-form-item label="密码">
              <el-input v-model="password" show-password></el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-button type="primary" plain @click="login()">登录</el-button>
            <el-button type="primary" plain @click="reg()">注册</el-button>
          </el-col>
        </el-row>
      </el-form>
      <form action="" v-else>
        用户名 <input type="text" v-model="name">
        密码 <input type="password" v-model="password">
        再输一次 <input type="password" v-model="repeat">
        <el-button type="primary" plain @click="addUser()">确定</el-button>
        <el-button type="primary" plain @click="cancel()">取消</el-button>
      </form>
    </el-main>
  </el-container>
</template>

<script>
  export default {
    name: 'Login',
    data () {
      return {
        isReg: false,
        name: '',
        password: '',
        repeat: ''
      }
    },
    methods: {
      login (formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!')
          } else {
            console.log('error submit!!')
            return false
          }
        })
        if (localStorage.getItem('name') === this.name && localStorage.getItem('password') === this.password) {
          this.name = ''
          this.password = ''
          this.$router.push('/home')
        } else {
          this.$message({
            showClose: true,
            type: 'error',
            message: '两次输入密码不一致'
          })
        }
      },
      reg () {
        this.isReg = true
      },
      addUser () {
        if (this.password === this.repeat) {
          localStorage.setItem('name', this.name)
          localStorage.setItem('password', this.password)
          this.name = ''
          this.password = ''
          this.isReg = false
        } else {
          alert('两次输入密码不一致')
        }
      },
      cancel () {
        this.isReg = false
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

<template>
  <el-container>
    <el-header></el-header>
    <el-main>
      <el-row>
        <el-form label-width="40px">
          <el-form-item label="标题">
            <el-input v-model="title"></el-input>
          </el-form-item>
          <el-form-item label="内容">
            <el-input type="textarea" :rows="5" v-model="content"></el-input>
          </el-form-item>
          <el-button type="primary" @click="add" class="el-width90">提交</el-button>
        </el-form>
      </el-row>
    </el-main>
    <el-footer></el-footer>
  </el-container>
</template>

<script>
  import store from '@/store'
  export default {
    name: 'Add',
    data () {
      return {
        title: '',
        content: ''
      }
    },
    methods: {
      add () {
        store.commit('addItem', {
          title: this.title,
          content: this.content
        })
        this.title = ''
        this.content = ''
        this.$router.push('/home/list')
      }
    }
  }
</script>

<style scoped>
  .el-width90 {
    width: 90%;
  }
</style>

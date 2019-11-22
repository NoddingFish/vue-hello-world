<template>
  <el-container>
    <el-header></el-header>
    <el-main>
      <el-row>
        <el-col :span="24">
          <img src="https://cn.vuejs.org/images/logo.png" width="200px;" alt="">
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="24">
          <h2>当前用户：{{ name }}</h2>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="24">
          <router-link :to="{name: 'add'}">
            <el-button class="el-width90" type="success">添加</el-button>
          </router-link>
        </el-col>
      </el-row>
    </el-main>
    <el-footer></el-footer>
  </el-container>
</template>

<script>
  export default {
    name: 'User',
    data() {
      return {
        name: localStorage.getItem('name')
      }
    }
  }
</script>

<style scoped>
  .el-width90 {
    width: 90%;
  }
</style>

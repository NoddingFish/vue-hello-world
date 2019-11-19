<template>
  <el-container direction="vertical">
    <el-header>
    </el-header>
    <el-main>
      <div>
        <router-view/>
      </div>
    </el-main>
    <el-footer>
      <el-row>
        <el-col :span="12">
          <router-link :to="{name: 'list'}">
            <el-button :span="24" type="primary">新闻列表</el-button>
          </router-link>
        </el-col>
        <el-col :span="12">
          <router-link :to="{name: 'user'}">
            <el-button type="primary">个人中心</el-button>
          </router-link>
        </el-col>
      </el-row>
    </el-footer>
  </el-container>
</template>

<script>
  export default {
    name: 'Home'
  }
</script>

<style scoped lang="scss">

  html, body, #app, .el-container {
    padding: 0;
    margin: 0;
    width: 100%;
    height: 100% !important;
  }

  el-footer{
    margin-bottom: 0px;
  }
</style>

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
      <div>
        <ul>
          <li>
            <router-link :to="{name: 'list'}">新闻列表</router-link>
          </li>
          <li>
            <router-link :to="{name: 'user'}">个人中心</router-link>
          </li>
        </ul>
      </div>
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
    width:100%;
    height: 100% !important;
  }

  a {
    color: #42b983;
    display: block;

    &.active {
      color: white;
      background-color: #42b983;
    }
  }
</style>

<template>
  <el-container>
    <el-header></el-header>
    <el-main>
      <el-card v-for="(item, index) in pageLists" :key="index" :body-style="{margin:'0px',padding:'10px',height: '80px'}" shadow="hover">
        <div style="padding: 14px;text-align: left">
          <span style="font-size: 18px;font-weight: bold;">{{item.title}}</span>
          <hr>
          <p>{{item.content}}</p>
        </div>
      </el-card>
    </el-main>
    <el-footer></el-footer>
  </el-container>
</template>

<script>
  import store from '@/store'
  export default {
    name: 'List',
    store,
    computed: {
      pageLists () {
        return store.state.lists
      }
    }
  }
</script>

<style scoped>

</style>

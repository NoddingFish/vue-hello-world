<template>
  <div>
    标题
    <input type="text" v-model="title">
    内容
    <input type="text" v-model="content">

    <el-button @click="add">提交</el-button>
  </div>
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

</style>

<template>
  <div id="home">
    <!-- slot="center" 确定要在哪里插入内容 在slot标签中要设置对应的name属性-->
      <Home></Home>
  </div>
</template>

<script>
import Home from 'views/home/Home.vue'
export default {
  components: {
    Home
  }
}
</script >

<style scoped>
</style>

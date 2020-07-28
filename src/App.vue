<template>
  <div id="home">
    <!-- slot="center" 确定要在哪里插入内容 在slot标签中要设置对应的name属性-->
      <!-- <Home></Home> -->
      <Cart></Cart>
      <!-- <Project></Project> -->
      <!-- <route-view></route-view> -->
      <main-tab-bar></main-tab-bar>
  </div>
</template>

<script>
// import Home from 'views/home/Home.vue'
import Cart from 'views/cart/Cart.vue'
// import Project from 'views/project/project.vue'
import MainTabBar from 'components/content/tabbar/MainTabBar'
export default {
  name: 'app',
  components: {
    // Home,
    // Project,
    Cart,
    MainTabBar
  }
}
</script >

<style>
 @import 'assets/css/reset.css';
</style>

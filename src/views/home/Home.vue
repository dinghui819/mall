<template>
  <div id="home">
    <!-- slot="center" 确定要在哪里插入内容 在slot标签中要设置对应的name属性-->
      <navBar class="home-nav"><div slot="center">购物街</div></navBar>
  </div>
</template>
<script>
import navBar from 'components/common/navbar/navBar.vue'
export default {
  components: {
    navBar
  }
}
</script >

<style scoped>
   #home{
       padding-top: 44px;
   }
  .home-nav{
    background: #0cec44;
    color: #fff;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index:9;
  }
  .tab-control{
      position: sticky;
      top: 44px;
  }
</style>

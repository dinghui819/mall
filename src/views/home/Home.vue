<template>
  <div id="home">
    <!-- slot="center" 确定要在哪里插入内容 在slot标签中要设置对应的name属性-->
      <navBar class="home-nav"><div slot="center">购物街</div></navBar>
      <TabControl class="tab-control" :titles="['流行','新款','精选']"></TabControl>
  </div>
</template>
<script>
import navBar from 'components/common/navbar/navBar.vue'
import TabControl from 'components/content/tabControl/TabControl.vue'
export default {
  components: {
    navBar,
    TabControl
  }
}
</script >

<style scoped>
   #home{
       padding-top: 44px;
   }
  .home-nav{
    background: #f10180;
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

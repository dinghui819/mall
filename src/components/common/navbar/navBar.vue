<template>
  <div class="nav-bar">
      <!-- 因为要对slot进行布局，所以在外面包一个div -->
      <div class="left"><slot name="left"></slot></div>
      <div class="center"><slot name="center"></slot></div>
      <div class="right"><slot name="right"></slot></div>
  </div>
</template>

<script>
export default {
}
</script>
<style scoped>
    .nav-bar{
        display: flex;
        text-align: center;
        /* 不设置高度，只设置行高时，组件没内容设置的效果不会显示 */
        height: 44px;
        line-height: 44px;
        box-shadow: 0 2px 2px rgba(100, 100, 100, .9)
        /* background: red; */
    }
    .left, .right{
        width: 60px;
        /* background: burlywood; */
    }
    /* 当其它的宽度为固定的值时，设置flex：1，就会实现，左右宽度固定，中间的宽度自适应 */
    .center{
       flex: 1; 
    }
</style>

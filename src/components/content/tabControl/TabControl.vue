<template>
  <div class="tab-control">
      <div v-for="(item, index) in titles" :key="index" 
      :class="{active:currentIndex===index}" 
      class="tab-control-item"
      @click="itemClick(index)">
          <span>{{item}}</span>
      </div>
  </div>
</template>

<script>
export default {
    props: {
        // 用的时候只需要传文字就行
        titles: {
            type:Array,
            default () {
                return []
            }
        }
    },
    //tab选中时的操作
    data() {
        return {
            currentIndex:0
        }
    },
    methods: {
        // tab点击切换
        itemClick (index) {
            this.currentIndex = index
        }
    },
}
</script>
<style scoped>
    .tab-control{
        display: flex;
        text-align: center;
        font-size: 15px;
        height: 40px;
        line-height: 40px;
        background: #fff;
    }
    .tab-control-item{
        flex: 1;
    }
    .tab-control-item span{
        padding-bottom: 2px; 
    }
    .active{
        color: #f10180;
       
    }
    .active span{
         border-bottom: 2px solid #f10180;
    }
</style>

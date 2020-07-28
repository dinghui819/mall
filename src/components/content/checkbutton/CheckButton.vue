<template>
  <div class="check-button" >
    <img src="~assets/img/cart/tick.svg" alt="" :class="{check: isCheck}">
  </div>
</template>

<script>
  export default {
    name: "CheckButton",
    props:{
      isCheck:{
        type:Boolean,
        default:false
      }
    }
  }
</script>

<style scoped>
  .check-button img{
    -webkit-border-radius: 50%;
    -moz-border-radius: 50%;
    border-radius: 50%;
    border:0.5px solid #11e747;
    vertical-align: middle;
    margin-bottom: 6px;
  }
  .check {
    border:0.5px solid #11e747!important;
    background-color:  #11e747;
  }
</style>

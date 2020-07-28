<template>
  <div id="cart">
    <!-- slot="center" 确定要在哪里插入内容 在slot标签中要设置对应的name属性-->
      <navBar class="home-nav">
          <div slot="left">←</div>
          <div slot="center">购物车</div>
          <div slot="right" @click="message">{{conTitle}}</div>
      </navBar>
       <div class="cart-box">
         <div class="cart_item" v-for="(item, index) in goodsList" :key=index>
           <!-- 店铺名称 -->
           <div class="item-selector">
             <div class="check-button" @click="changeCheck(index, $event)">
                <img src="~assets/img/cart/tick.svg" alt="" :class="{check: isCheck}">
             </div>
             <!-- <check-button :is-check="product.isCheck" @click.native="changeCheck"></check-button> -->
             <div>{{item.storeName}} ></div>
           </div>
           <!-- 商品 -->
           <div class="goods-item">
             <div class="select item-selector">
               <div class="check-button" @click="changeCheck(index)">
                  <img src="~assets/img/cart/tick.svg" alt="" :class="{check: isCheck}">
               </div>
               <!-- <check-button :is-check="product.isCheck" @click.native="changeCheck"></check-button> -->
             </div>
             <div class="img">
               <img :src="item.img" alt="">
             </div>
             <div class="goods-desc">
               <p class="name">{{item.name}}</p>
               <span class="desc">{{item.desc}}</span>
               <div class="price-box">
                 <div class="price">￥{{item.price}}</div>
                 <div class="btn-box">
                   <span class="subBtn btn" @click="subBtn">-</span>
                   <span class="btn">{{count}}</span>
                   <span class="addBtn btn" @click="addBtn">+</span>
                 </div>
               </div>
             </div>
           </div>
         </div>
       </div>
       <div class="cart-bottom-bar">
          <div class="total-check">
            <div class="check-button" @click="selectAll">
                <img src="~assets/img/cart/tick.svg" alt="" :class="{check: isCheck}">
            </div>
            <span>全选</span>
          </div>
          <div :class="{'total-price':!flag, 'move': flag}">
            <span>{{total}}</span>
          </div>
          <div :class="{'calc':!flag, 'delete': flag}">
            {{settlement}} {{price}}
          </div>
        </div>
  </div>
</template>
<script>
import navBar from 'components/common/navbar/navBar.vue'
import CheckButton from 'components/content/checkbutton/CheckButton'
export default {
  data () {
    return {
      goodsList:[{
        id:0,
        storeName: "红鑫羽生鲜专营店",
        img: require('../../assets/img/tabbar/fresh.jpg'),
        name: "新鲜现在纯碱 带向10斤装 生鲜水果",
        desc: "果粒饱满多字 甜蜜爆炸",
        price: 129
      // },
      //  {
      //   id:1,
      //   storeName: "红鑫羽生鲜专营店",
      //   img: require('../../assets/img/tabbar/fresh.jpg'),
      //   name: "新鲜现在纯碱 带向10斤装 生鲜水果",
      //   desc: "果粒饱满多字 甜蜜爆炸",
      //   price: 129
      // }, 
      // {
      //   id:2,
      //   storeName: "红鑫羽生鲜专营店",
      //   img: require('../../assets/img/tabbar/fresh.jpg'),
      //   name: "新鲜现在纯碱 带向10斤装 生鲜水果",
      //   desc: "果粒饱满多字 甜蜜爆炸",
      //   price: 129
      // },  {
      //   id:3,
      //   storeName: "红鑫羽生鲜专营店",
      //   img: require('../../assets/img/tabbar/fresh.jpg'),
      //   name: "新鲜现在纯碱 带向10斤装 生鲜水果",
      //   desc: "果粒饱满多字 甜蜜爆炸",
      //   price: 129
      }],
      count: 1,
      conTitle: "管理",
      total: "合计：0",
      settlement: "结算",
      flag: false,
      isCheck: false,
      price: 0
    }
  },
  methods: {
    message(){
      this.flag = !this.flag
      if (this.flag == true) {
        this.conTitle = "完成"
        this.settlement = "删除"
        this.total = "移入收藏夹"
        this.isCheck = true
        this.price = ''
      } else {
        this.conTitle = "管理"
        this.settlement = "结算"
        this.total = "合计：0"
        this.isCheck = false
        this.price = (0)
      }
    },
    subBtn () {
      if (this.count > 0){
        this.count--
      }
    },
    addBtn () {
      this.count++
    },
    changeCheck (index) {
        if(this.goodsList[index].id == index){
           this.isCheck = !this.isCheck
        } 
    },
    // getPrice () {
    //   if (this.isCheck = true) {
    //      this.goodsList.forEach(item => {
    //        this.price = item.price 
    //      })
    //    }
    // },
    selectAll () {
      this.isCheck = !this.isCheck
    }
  },
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
  .cart-box{
    margin-top: 44px;
    background: #f2f2f2;
    margin-bottom: 69px;
    padding:20px;
  }
  .cart_item{
    background-color: #fff;
    padding: 10px;
    border-radius: 10px;
    margin: 10px 0;
  }
  .check-button img,
  .goods-item select .check-button img{
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
  .check-button{
    margin-bottom: 0;
    margin-top: 3px;
    padding-right: 5px;
  }
  .item-selector {
    font-size: 14px;
    letter-spacing: 1px;
    color: #464343;
    display: flex;
    padding: 5px;
    line-height: 28px;
    align-items: center;
  }
  .goods-item{
    display: flex;
    align-items: center;
  }
  .goods-item select {
    padding-top: 20px;
  }
  .goods-item select .check-button img{

  }
  .goods-item .img img{
    width: 86px;
    height: 86px;
    margin:0 10px;
  }
  .goods-item .goods-desc{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
     line-height:1.5;
  }
  .goods-item .goods-desc .name{
    font-size: 14px;
    height: 38px;
   
    overflow: hidden;
  }
  .goods-item .goods-desc .desc{
    background-color: #f2f2f2;
    color: grey;
    font-size: 10px;
    margin: 10px 0;
  }
  .goods-item .goods-desc .price-box{
    display: flex;
    justify-content: space-between;
  }
  .goods-item .goods-desc .price-box .price{
    color: red;
  }
  .goods-item .goods-desc .price-box .btn-box .btn{
    text-align: center;
    display: inline-block;
    width: 25px;
    height: 25px;
    line-height: 22px;
    border: 1px solid #0cec44;
    color:#0cec44 ;
  }
  .goods-item .goods-desc .price-box .btn-box .btn:nth-child(2){
    border-left: none;
    border-right: none;
  }
  .cart-bottom-bar {
    width: 100%;
    height: 40px;
    position: fixed;
    bottom: 49px;
    background: #fff;
    display: flex;
    line-height: 40px;
    text-align: center;
    border-top:1px solid #f2f2f2 ;
    align-items: center;
  }
  .total-check {
    padding-left: 27px;
    flex: 1;
    display: flex;
  }
  .total-price {
    flex: 1;
  }
  .move{
    flex: 1;
    border: 1px solid #f7db5f;
    color: #f7db5f;
    height: 30px;
    line-height: 30px;
    border-radius: 40px;
  }
  .calc {
    height: 30px;
    line-height: 30px;
    flex: 1;
    background-color: #ff5028;
    color:#fff;
    border-radius: 40px;
    margin: 0px 20px 0px 5px;
  }
  .delete{
    height: 30px;
    line-height: 30px;
    flex: 0.5;
    border-radius: 40px;
    margin: 0px 20px 0px 5px;
    border: 1px solid #ff5028;
    color: #ff5028;
  }
</style>

<template>
   <div class="weekend">
     <h2 class="title">周末去哪儿</h2>
     <div>
       <div class="product-item" v-for="item in weekendList" :key="item.id">
         <a href="###">
             <div class="product-img">
               <img :src="item.imgUrl" :alt="item.title">
             </div>
           <div class="product-info">
             <p class="product-name">{{item.title}}</p>
             <p class="product-desc">{{item.desc}}</p>
           </div>
         </a>
       </div>
     </div>
   </div>
</template>

<script>
export default {
  name: 'Weekend',
  props: {
    weekendList: {
      type: Array
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/mixins.styl"
  @import "~styles/varibles.styl"
  .weekend{
    .title{
      height .8rem
      padding-left .26rem
      line-height .8rem
      color $darkTextColor
      background #f1f1f1
    }
    .product-item {
      .product-img {
        overflow hidden
        height 0
        padding-bottom 37.4375%
        img {
          width 100%
        }
      }
      .product-info {
        padding .14rem .2rem .2rem .2rem
        .product-name,.product-desc{
          padding-right 1.4rem
          color $darkTextColor
          font-size .28rem
          line-height .48rem
          ellipsis()
        }
        .product-desc{
          color $smallTextColor
        }
      }
    }
  }
</style>

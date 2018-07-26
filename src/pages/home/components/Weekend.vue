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
  data () {
    return {
      weekendList: [
        {
          id: '00001',
          title: '杭州必游TOP10',
          imgUrl: 'http://img1.qunarzz.com/sight/source/1505/4e/3e87ee62e59cdb.jpg_r_640x214_fe6cc902.jpg',
          desc: '杭州，前世今生与你有一场美丽约会'
        },
        {
          id: '000002',
          title: '承载杭城的历史之地',
          imgUrl: 'http://img1.qunarzz.com/sight/source/1505/9f/7d45cc38259e0.jpg_r_640x214_156f4299.jpg',
          desc: '饱经沧桑的地方诉述着这座城的段段衷肠'
        },
        {
          id: '000003',
          title: '杭州多样乐园',
          imgUrl: 'http://img1.qunarzz.com/sight/source/1505/bc/83feb2e003d0dd.jpg_r_640x214_0b7269b8.jpg',
          desc: '这个周末终于可以陪宝贝去玩耍啦'
        }
      ]
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

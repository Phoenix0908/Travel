<template>
  <div class="hot-recommend">
    <div class="gap"></div>
    <div class="title-content">
      <img src="http://img1.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png" alt="本周热门榜单">
      <span class="title">本周热门榜单</span>
      <a class="more" href="http://touch.piao.qunar.com/touch/weekHotSales.htm?cityName=杭州">
        全部榜单
        <span class="iconfont">&#xe601;</span>
      </a>
    </div>
    <ul class="hot-list">
      <li class="hot-content" v-for="(item,index) in hotList" :key="item.id">
        <div class="hot-img-tag" v-if="index === 0">
          <img src="http://img1.qunarzz.com/piao/fusion/1710/ab/159673b63e6ca702.png" alt="">
        </div>
        <div class="hot-img-tag" v-else-if="index ===1">
          <img src="http://img1.qunarzz.com/piao/fusion/1710/2d/36d0c4adaebbbc02.png" alt="">
        </div>
        <div class="hot-img-tag" v-else-if="index ===2">
          <img src="http://img1.qunarzz.com/piao/fusion/1710/67/edc47ffef9e96b02.png" alt="">
        </div>
        <div class="hot-imgcon">
         <img :src="item.imgUrl" :alt="item.title">
        </div>
        <div class="hot-content-title">{{item.title}}</div>
        <div class="price"><span>¥<em>{{item.price}}</em></span>起</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    hotList: {
      type: Array
    }
  },
  data () {
    return {
      show: false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .gap{
    gap()
  }
.hot-recommend{
  .title-content{
    width 100%
    padding .24rem 0
    img{
      width .3rem
      margin-left .2rem
      vertical-align top
    }
    .title{
      display inline-block
      font-size .32rem
      color $darkTextColor
    }
    .more{
      display inline-block
      vertical-align top
      float right
      margin-right .2rem
      color $darkTextColor
      font-size .24rem
    }
  }
  .hot-list{
    padding 0 .2rem
    overflow-x scroll
    white-space: nowrap
    .hot-content{
      position relative
      width 2rem
      padding  .06rem .2rem .2rem 0
      display inline-block
      .hot-img-tag{
        position absolute
        top 0
        left 0
        z-index 10
        width .84rem
        height .4rem
        img{
          width 100%
        }
      }
      .hot-imgcon{
        overflow hidden
        width 2rem
        height 0
        padding-bottom 100%
        img{
          width 100%
        }
      }
      .hot-content-title{
        color: $darkTextColor;
        font-size: .24rem;
        line-height: .32rem;
        text-align: center;
        ellipsis()
      }
      .price{
        color: #616161;
        font-size: .24rem;
        line-height: .36rem;
        text-align: center;
        span{
          color: $priceTextColor
        }
      }
    }
  }
}
</style>

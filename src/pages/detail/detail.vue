<template>
    <div class="detail">
      <div class="header">
        <router-link tag="div" to="/" class="header-abs" v-show="showabs">
          <span class="iconfont back-icon">&#xe624;</span>
        </router-link>
        <div class="header-fixed" v-show="!showabs" :style="opacityStyle">
          <router-link :to="{path: '/'}" class="icon"><span class="iconfont back-icon">&#xe624;</span></router-link>
          <h1>{{sightName}}</h1>
        </div>
      </div>
      <div class="banner-wrap" @click="handleShowGallary">
        <div class="banner">
          <img :src="bannerImg" alt="">
        </div>
      </div>
      <div class="detail-baseInfo">
        <div class="baseInfo-card">
          <div class="baseInfo-card-left">
            <div>
              <span class="commentcard-score">5.0</span>
              <span class="commentcard-text">分</span>
              <span class="commentcard-desc">超赞</span>
            </div>
            <div>
              <span class="totalcommentnum">170029条评论</span>
              <span class="totalcommentnum">32条攻略</span>
            </div>
            <span class="iconfont arrow">&#xe601;</span>
          </div>
          <div class="baseInfo-card-right">
            <p class="sightcard-title">景点简介</p>
            <p class="sightcard-text">开放时间、贴士</p>
            <span class="iconfont arrow">&#xe601;</span>
          </div>
        </div>
        <div class="baseInfo-address">
          <span class="iconfont address-icon">&#xe602;</span>
          <span class="address-location">上海市浦东新区川沙新镇上海迪士尼度假区内尼度假区内</span>
          <span class="iconfont address-arrow">&#xe601;</span>
        </div>
      </div>
      <CommonGallary :imgs="gallaryImgs" v-show="showGallary" @close="handleCloseGallary"></CommonGallary>
      <DetailList :list="categoryList"></DetailList>
      <div class="content"></div>
    </div>
</template>

<script>
import CommonGallary from '@/components/gallary'
import DetailList from './components/list'
import axios from 'axios'

export default {
  name: 'detail',
  components: {
    CommonGallary, DetailList
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      categoryList: [],
      showGallary: false,
      showabs: true,
      opacityStyle: 0
    }
  },
  mounted () {
    this.getDetailInfo()
    window.addEventListener('scroll', this.handleScroll)
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.handleGeyDataSucc)
    },
    handleGeyDataSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.categoryList = data.categoryList
      }
    },
    handleShowGallary () {
      this.showGallary = true
    },
    handleCloseGallary () {
      this.showGallary = false
    },
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showabs = false
      } else {
        this.showabs = true
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/mixins.styl"
  @import "~styles/varibles.styl"
  * { touch-action: none }
  .detail{
  .header{
    .header-abs{
      position absolute
      left .2rem
      top .2rem
      width .72rem
      height .72rem
      line-height .8rem
      border-radius 50%
      background #000000
      opacity .5
      text-align center
      .back-icon{
        font-size .4rem
        color #fff
      }
    }
    .header-fixed{
      position fixed
      top 0
      left 0
      right 0
      line-height .86rem
      background $bgColor
      color #fff
      text-align center
      z-index 99
      .icon{
        display inline-block
        position absolute
        top 0
        left 0
        width .64rem
        .back-icon{
          font-size 14px
          color #fff
        }
      }
      h1{
        margin 0 .64rem
        font-size .32rem
        ellipsis()
      }
    }
  }
  .banner-wrap{
    .banner{
      overflow hidden
      height 0
      padding-bottom 55%
      img{
        width 100%
      }
    }
  }
  .detail-baseInfo{
    position relative
    top -.1rem
    padding .1rem .2rem 0 .2rem
    margin-bottom .1rem
    background #fff
    border-radius .1rem .1rem 0 0
    .baseInfo-card{
      padding-top .1rem
      padding-bottom .2rem
      display flex
      .baseInfo-card-left{
        flex 1
        color $priceTextColor
        position relative
        .commentcard-score{
          font-size .44rem
          line-height .44rem
        }
        .commentcard-text{
          font-size .28rem
          line-height: .48rem
        }
        .commentcard-desc{
          margin-left .2rem
          font-size .28rem
          line-height: .48rem
        }
        .totalcommentnum{
          font-size .24rem
          color #9e9e9e
          line-height .32rem
          margin-right .2rem
        }
        .arrow{
          position absolute
          top .3rem
          right .2rem
          color #9e9e9e
          font-size .24rem
        }
      }
      .baseInfo-card-right{
        position relative
        flex 1
        &:before{
          position absolute
          top 0
          left 0
          width 1px
          height 100%
          border-left: 1px solid #ddd
          content:  ''
        }
        .sightcard-title{
          font-size .28rem
          color $darkTextColor
          line-height .48rem
          padding-left .3rem
        }
        .sightcard-text{
          color $smallTextColor
          line-height .24rem
          padding-left .3rem
        }
        .arrow{
           position absolute
           top .3rem
           right .2rem
           color #9e9e9e
           font-size .24rem
        }
      }
    }
    .baseInfo-address{
      padding .2rem 0
      line-height .36rem
      color $darkTextColor
      border-1px-top(#f0f0ef)
      .address-icon{
        color #9e9e9e
        font-size .32rem
        vertical-align top
      }
      .address-location{
        display inline-block
        width 80%
        ellipsis()
      }
      .address-arrow{
        float right
        color #9e9e9e
      }
    }
  }
  .content{
    height 50rem
  }
}
</style>

<template>
  <div class="city">
    <div class="city-header">
      <router-link :to="{path: '/'}" class="icon"><span class="iconfont back-icon">&#xe624;</span></router-link>
      <h1>城市选择</h1>
    </div>
    <div class="city-list" ref="wrapper">
      <div>
        <div class="area">
          <h3>热门城市</h3>
          <ul class="area-list list-tr3">
            <li v-for="item of hotCity" :key="item.id" @click.prevent="handleCityClick(item.name)">{{item.name}}</li>
          </ul>
        </div>
        <div class="area">
          <h3>字母排序</h3>
          <ul class="character-list">
            <li v-for="item in letters" :key="item" @click="handleLetterClick">{{item}}</li>
          </ul>
        </div>
        <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
          <h3>{{key}}</h3>
          <ul class="area-list">
            <li v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import BScroll from 'better-scroll'
import {mapMutations} from 'vuex'

export default {
  name: 'City',
  data () {
    return {
      hotCity: [],
      cities: {}
    }
  },
  mounted () {
    this.getCityInfo()
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json')
        .then(this.handleGetCityInfo)
    },
    handleGetCityInfo (res) {
      res = res.data
      if (res.ret && res.data) {
        this.hotCity = res.data.hotCities
        this.cities = res.data.cities
      }
    },
    handleLetterClick (e) {
      const clickTest = e.target.innerText
      const element = this.$refs[clickTest][0]
      this.scroll.scrollToElement(element)
    },
    handleCityClick (city) {
      // this.$store.dispatch('changeCity', city)
      // this.$store.commit('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .city{
    .city-header{
      position relative
      line-height .86rem
      background $bgColor
      color #fff
      text-align center
      z-index 999
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
    .city-list{
      position absolute
      top .86rem
      left 0
      right 0
      bottom 0
      .area{
        h3{
          background #f1f1f1
          font-size .24rem
          padding  .24rem .3rem
        }
        .character-list{
          overflow: hidden;
          background-color: #fff;
          padding: .3rem 0;
          z-index 20
          li{
            width: 16.66%;
            height: .9rem;
            line-height: .9rem;
            font-size: .28rem;
            text-align: center;
            float: left;
            color: $darkTextColor;
          }
        }
        .area-list{
          width 100%
          overflow hidden
          position relative
          z-index 99
          li{
            width 25%
            border-bottom 1px solid #ddd
            height .9rem
            line-height .9rem
            font-size .28rem
            text-align center
            float left
          }
          &:before{
            content ''
            position absolute
            width: 25%
            left: 25%
            height: 100%
            border-left: .02rem solid #ddd
            border-right: .02rem solid #ddd
            z-index -1
          }
          &:after{
            content ''
            position absolute
            width 10%
            left 75%
            height 100%
            border-left .02rem solid #ddd
            border-right 0
            z-index -1
          }
          .border-none{
            border-bottom none
          }
        }
        .list-tr3{
          li{
            width 33.3%
          }
          &:before{
            width 33.33%
            left 33.33%
          }
          &:after{
            border 0
          }
        }
      }
    }
  }
</style>

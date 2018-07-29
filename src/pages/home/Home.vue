<template>
    <div>
      <HomeHeader></HomeHeader>
      <HomeSwiper :swiperList="swiperList"></HomeSwiper>
      <HomeIcons :iconList="iconList"></HomeIcons>
      <HomeRecommend :hotList="hotList"></HomeRecommend>
      <HomeLike :likeList="likeList"></HomeLike>
      <HomeWeekend :weekendList="weekendList"></HomeWeekend>
    </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeLike from './components/Like'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import {mapState} from 'vuex'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeLike,
    HomeWeekend
  },
  data () {
    return {
      swiperList: [],
      iconList: [],
      hotList: [],
      likeList: [],
      weekendList: [],
      lastCity: ''
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeSucc)
    },
    getHomeSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.hotList = data.hotList
        this.likeList = data.likeList
        this.weekendList = data.weekendList
      }
    }
  },
  mounted () {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style scoped>
</style>

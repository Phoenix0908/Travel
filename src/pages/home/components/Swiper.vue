<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <swiper-slide v-for="item in swiperList" :key="item.id"><img :src="item.imgUrl" class="swiper-img"></swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    swiperList: {
      type: Array
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        },
        loop: true,
        autoplay: true,
        speed: 400
      }
    }
  },
  computed: {
    showSwiper () {
      return this.swiperList.length
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active{
    background #fff
  }
  .wrapper{
    overflow hidden
    width 100%
    //height 31.25vw 这种写法，有些浏览器会有兼容问题
    height 0
    padding-bottom 26.67%
    background #f1f1f1
    .swiper-img{
      width 100%
    }
  }
</style>

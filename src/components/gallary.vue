<template>
  <div class="container" @click.stop="handleCloseGallary">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(item,index) in imgs" :key="index">
          <img :src="item" class="swiper-img">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'gallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination',
          type: 'fraction'
        },
        observer: true,
        observeParents: true
      }
    }
  },
  methods: {
    handleCloseGallary () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-pagination{
    color #fff
    bottom: -50px
  }
  .container >>>.swiper-container{
    overflow inherit
  }
.container{
  display flex
  flex-direction column
  justify-content center
  position fixed
  top 0
  left 0
  bottom 0
  right 0
  background #000000
  z-index 99
  .wrapper{
    width 100%
    .swiper-img{
      width 100%
    }
  }
}
</style>

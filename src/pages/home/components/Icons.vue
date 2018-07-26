<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) of pages" :key="index">
        <div class="icon" v-for="item in page" :key="item.id">
          <img :src="item.imgUrl" alt="">
          <p>{{item.desc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    iconList: {
      type: Array
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        }
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .icons >>> .swiper-pagination-bullet-active{
    background $bgColor
  }
  .icons >>> .swiper-container{
    padding-bottom .6rem
  }
.icons{
  width 100%
  padding 0.1rem 0
  .icon{
    float left
    width 25%
    height 1.5rem
    text-align center
    padding-top: .1rem
    img{
      width 1.1rem
    }
    p{
      margin-top .1rem;
      color $darkTextColor;
      font-size .28rem
      ellipsis()
    }
  }
}
</style>

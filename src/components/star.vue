<template>
  <div class="star" :class="starType">
    <span v-for="(itemclass,index) in itemClasses" :class="itemclass" class="star-item" :key="index"></span>
  </div>
</template>

<script type="text/ecmascript-6">
const length = 5
const clson = 'on'
const clsoff = 'off'
const clshalf = 'half'

export default {
  props: {
    size: {
      type: Number
    },
    score: {
      type: Number
    }
  },
  computed: {
    starType () {
      return 'star-' + this.size
    },
    itemClasses () {
      let result = []
      let score = Math.floor(this.score * 2) / 2
      let haoDecimal = score % 1 !== 0
      let integer = Math.floor(score)
      for (let i = 0; i < integer; i++) {
        result.push(clson)
      }
      if (haoDecimal) {
        result.push(clshalf)
      }
      while (result.length < length) {
        result.push(clsoff)
      }
      return result
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet">
  @import '"~styles/mixins'
.star{
  font-size 0
  display inline-block
  .star-item{
    display inline-block
    background-repeat no-repeat
  }
  &.star-48{
    .star-item{
      width .22rem
      height .22rem
      margin-right 2px
      background-size .22rem .22rem
      &:last-child{
        margin-right 0
      }
      &.on{
        bg-img2('star48_on')
      }
      &.half{
        bg-img2('star48_half')
      }
      &.off{
        bg-img2('star48_off')
      }
    }
  }
  &.star-36{
    .star-item{
      width .15rem
      height .15rem
      margin-right 6px
      background-size .15rem .15rem
      &:last-child{
        margin-right 0
      }
      &.on{
        bg-img2('star36_on')
      }
      &.half{
        bg-img2('star36_half')
      }
      &.off{
        bg-img2('star36_off')
      }
    }
  }
  &.star-24{
    .star-item{
      width .1rem
      height .1rem
      margin-right 3px
      background-size .1rem .1rem
      &:last-child{
        margin-right 0
      }
      &.on{
        bg-img2('star24_on')
      }
      &.half{
        bg-img2('star24_half')
      }
      &.off{
        bg-img2('star24_off')
      }
    }
  }
}
</style>

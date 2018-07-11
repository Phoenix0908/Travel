<template>
    <div class="header">
      <div class="header-left">
        <span class="iconfont back-icon">&#xe624;</span>
      </div>
      <div class="header-input">
        <span class="iconfont">&#xe632;</span>
        <input type='text' placeholder="输入城市/景点/游玩主题">
      </div>
      <div class="header-right">
        城市
        <span class="iconfont arrow-icon">&#xe600;</span>
      </div>
    </div>
</template>

<script>
export default {
  name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
@import "~styles/varibles.styl"
.header {
  display flex
  line-height .86rem
  background $bgColor
  color #fff
  .header-left {
    width .64rem
    float left
    text-align center
    .back-icon{
      font-size 14px
    }
  }
  .header-input{
    flex 1
    height .64rem
    line-height .64rem
    margin-top .12rem
    background #ffffff
    border-radius .1rem
    color #cccccc
    padding 0 0.1rem
    input{
      width 90%
      height 100%
      vertical-align top
    }
  }
  .header-right {
    width 1.24rem
    float right
    text-align center
    .arrow-icon{
      margin-left -.04rem
      font-size .24rem
    }
  }
}
</style>

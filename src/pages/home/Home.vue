<template>
    <div>
      <HomeHeader></HomeHeader>
      <HomeSwiper></HomeSwiper>
      <HomeIcons></HomeIcons>
      <HomeRecommend></HomeRecommend>
      <HomeLike></HomeLike>
      <HomeWeekend></HomeWeekend>
    </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeLike from './components/Like'
import HomeWeekend from './components/Weekend'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeLike,
    HomeWeekend
  }
}
</script>

<style scoped>
</style>

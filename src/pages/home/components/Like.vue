<template>
  <div class="you-like">
    <div class="gap"></div>
    <div class="title-content">
      <img src="http://img1.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png" alt="猜你喜欢">
      <span class="title">猜你喜欢</span>
    </div>
    <ul class="like-list">
      <li class="like-content" v-for="item in likeList" :key="item.id">
          <img class="like-img-tag" :src="item.imgUrl" :alt="item.title">
        <div class="like-info">
          <div class="like-title">{{item.title}}</div>
          <div class="like-comment">
            <Star :size="48" :score="item.score"></Star>
            <span class="like-commentNum">{{item.commentNum}}条评论</span>
          </div>
          <div class="like-price">
            <span class="mp-price">¥<span class="mp-priceNum">{{item.price}}</span></span>起
            <span class="mp-address">{{item.address}}</span>
          </div>
        </div>
      </li>
    </ul>
    <a href="###" class="like-more">查看所有产品</a>
  </div>
</template>

<script>
import Star from '@/components/star'
export default {
  name: 'Like',
  components: {
    Star
  },
  data () {
    return {
      likeList: [
        {
          id: '01',
          title: '上海迪士尼乐园',
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg',
          score: 4.6,
          commentNum: 165779,
          price: 69,
          address: '浦东新区'
        },
        {
          id: '02',
          title: '杭州云曼温泉',
          imgUrl: 'http://img1.qunarzz.com/sight/p0/201401/06/3fbbddda915cb7637439d484440d36be.jpg_200x200_a54e87dd.jpg',
          score: 4.2,
          commentNum: 946,
          price: 128,
          address: '萧山区'
        },
        {
          id: '03',
          title: '杭州浪浪浪水公园',
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1706/45/456c4be6ba4fa604a3.img.jpg_200x200_81d9a0be.jpg',
          score: 4.1,
          commentNum: 2247,
          price: 120,
          address: '萧山区'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~styles/mixins.styl"
@import "~styles/varibles.styl"
.you-like {
  .gap{
    gap ()
  }
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
  }
  .like-list{
    padding 0 .24rem
    .like-content{
      &:last-child{
        border-none()
      }
      padding .2rem 0
      display flex
      border-1px(#e0e0e0)
      .like-img-tag{
        height  2rem
      }
      .like-info{
        margin-left .22rem
        width 100%
        .like-title{
          margin-top .26rem
          height .44rem
          color: $darkTextColor
          font-size .32rem
          line-height .44rem
        }
        .like-comment{
          margin-top .14rem
          height .34rem
          .like-commentNum{
            color $smallTextColor
            font-size .24rem
            line-height .34rem
            vertical-align text-bottom
            margin-left .1rem
          }
        }
        .like-price{
          margin-top .22rem
          color $smallTextColor
          font-size .24rem
          line-height .4rem
          .mp-price{
            color $priceTextColor
            .mp-priceNum{
              font-size .4rem
            }
          }
          .mp-address{
            float right
          }
        }
      }
    }
  }
  .like-more{
    display block
    text-align center
    padding .1rem 0
    line-height .4rem
    color $bgColor
    font-size .28rem
    border-1px-top(#e0e0e0)
  }
}
</style>

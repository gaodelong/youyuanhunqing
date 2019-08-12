<template>
  <div class="container">
    <!--轮播图-->
    <Swiper :images="images"/>
    <div class="page-head-title">
      <van-icon name="bell" size="36rpx"  class="head-icon" />
      <!--<image class="head-icon" :src="headTitleImg"></image>-->
      <span class="head-text">{{headTitleText}}</span>
    </div>
    <!--最近作品-->
    <recentWorks></recentWorks>
    <!--关于我们-->
    <aboutUs></aboutUs>
  </div>
</template>

<script>
import Swiper from '@/components/swiper';
import recentWorks from '@/components/recent-works';
import aboutUs from '@/components/aboutUs/about-us';
export default {
  components: {
    Swiper,
    recentWorks,
    aboutUs
  },
  data () {
    return {
      images: [
        {
          url: '../../static/images/1.jpeg'
        },
        {
          url: '../../static/images/2.jpeg'
        },
        {
          url: '../../static/images/3.jpg'
        }
      ],
      headTitleImg: '../../static/images/lingdang.png',
      headTitleText: '一站式私人婚礼定制! 营业时间: 8:00 - 21:00'
    }
  },


  methods: {
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
  .page-head-title {
    height: 60rpx;
    line-height: 60rpx;
    padding-left: 20rpx;
    background-color: #fff;
  }
  .head-icon {
    color: #74E5D6;
    vertical-align: middle;
  }
  .head-text {
    font-size: 28rpx;
    margin-left: 25rpx;
    /*vertical-align: middle;*/
    color: #888888;
  }

</style>

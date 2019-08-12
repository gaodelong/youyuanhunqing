<template>
  <div class="about-us">
    <div class="headTitle">
      <span class="title">关于我们</span>
      <a @click="goAllUs">MORE</a>
    </div>
   <div class="about-us-content">
     <AboutUsSwiper :images="images"></AboutUsSwiper>
   </div>
  </div>
</template>

<script>
  import AboutUsSwiper from './about-us-swiper';

  export default {
    components: {
      AboutUsSwiper
    },
    data() {
      return {
        images: [
          {
            id: '1',
            title: '花艺师',
            url: '../../static/images/1.jpeg'
          },
          {
            id: '2',
            title: '灯光,统筹',
            url: '../../static/images/2.jpeg'
          },
          {
            id: '3',
            title: '策划',
            url: '../../static/images/3.jpg'
          },
          {
            id: '4',
            title: '司仪',
            url: '../../static/images/1.jpeg'
          }
        ]
      }
    },
    methods: {
      //跳转-所有我们
      goAllUs(){
        mpvue.navigateTo({
          url: `../../pages/all-us/main?title=关于我们`
        })
      }
    },
  }
</script>

<style lang="wxss">
  .about-us {
    margin-top: 20rpx;
    background: #fff;
  }
  .about-us .headTitle{
    height: 60rpx;
    line-height: 60rpx;
    display: flex;
    justify-content: space-between;
  }
  .about-us .headTitle .title{
    padding-left: 35rpx;
    position: relative;
    font-size: 32rpx;
    color: #060606;
  }
  .about-us .headTitle .title::before{
    content: ' ';
    position: absolute;
    left: 0;
    top: 0;
    display: inline-block;
    width: 8rpx;
    height: 100%;
    background: #BC4B31;
  }
  .about-us .headTitle a{
    margin-right: 10rpx;
    font-size: 26rpx;
    color: #8C8C8C;
  }
.about-us-content{
  height: 100%;
  padding: 0 10rpx;
  padding-bottom: 40rpx;
}
</style>

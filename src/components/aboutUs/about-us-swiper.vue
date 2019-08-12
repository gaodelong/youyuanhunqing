<template>
  <swiper class="swiper" :autoplay="false" :circular="false" :interval="3000" :duration="500" display-multiple-items="2">
    <block v-for="(item, index) in images" :key="index">
      <swiper-item class="swiper-item" @click="goAboutUsDetail(item)">
        <image :src="item.url" class="slide-image" />
        <h5 class="slide-title">{{item.title}}</h5>
      </swiper-item>
    </block>
  </swiper>
</template>

<script>
  export default {
    props: {
      images: Array
    },
    data () {
      return {
      }
    },
    methods:{
      //跳转关于我们详情页
      goAboutUsDetail(item){
        console.log('关于我们',item);
        let url = item.url;
        let id = item.id;
        let title = item.title;
        mpvue.navigateTo({
          url: `../aboutUs-detail/main?id=${id}&title=${title}&url=${url}`
        })
      }
    }
  }
</script>

<style scoped>
  .swiper {
    height: 290rpx !important;
  }
  .slide-image {
    height: 85%;
    width: 98%;
  }
  .swiper-item{
    margin:0 1% !important;
  }
  .slide-title{
    margin-top: -10rpx;
    color: #888888;
    font-size: 24rpx;
    text-align: center;
  }

</style>

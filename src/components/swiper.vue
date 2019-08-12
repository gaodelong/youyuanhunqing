<template>
  <swiper class="swiper" :indicator-dots="true" :autoplay="true" :circular="true" :interval="3000" :duration="500">
    <block v-for="(item, index) in images" :key="index">
      <swiper-item>
        <image :src="item.url" class="slide-image"/>
      </swiper-item>
    </block>
  </swiper>
</template>

<script>
  export default {
    props: {
      images: Array
    },
    data() {
      return {}
    },
    methods: {}
  }
</script>

<style scoped>
  .swiper {
    height: 240 rpx !important;
  }

  .slide-image {
    height: 100%;
    width: 100%;
  }
</style>

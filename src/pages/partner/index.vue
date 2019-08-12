<template>
  <div class="content">
   <ul>
     <li v-for="(item,key) in partner" :key="key">
       <a class="partner-item" @click="goPartnerDetail(item)">
         <img :src="item.url" alt="">
         <div class="partner-item-title">{{item.title}}</div>
       </a>
     </li>
   </ul>
  </div>
</template>

<script>

export default {

  data () {
    return {
      partner:[
        {
          url: '../../static/images/1.jpeg',
          title: 'xx摄影',
          id: '1'
        },
        {
          url: '../../static/images/2.jpeg',
          title: 'xx美妆',
          id: '2'
        },
        {
          url: '../../static/images/3.jpg',
          title: '测试测试',
          id: '3'
        },
        {
          url: '../../static/images/3.jpg',
          title: '一见钟情',
          id: '4'
        }
      ],
    }
  },

  created () {
  },
  methods: {
    //跳转详情页
    goPartnerDetail(item) {
      let url = item.url;
      let id = item.id;
      let title = item.title;
      mpvue.navigateTo({
        url: `../../pages/partner-detail/main?id=${id}&title=${title}&url=${url}`
      })
    }
  }
}
</script>

<style scoped>
.content{
  padding: 10rpx;
}
.content ul >li a{
  width: 100%;
  height: 340rpx;
  position: relative;
}
  .content ul> li a img{
    width: 100%;
    height: 330rpx;
  }
.content  ul >li a .partner-item-title{
  height: 40rpx;
  line-height: 40rpx;
  width: 100%;
  position: absolute;
  bottom: 10rpx;
  left: 0;
  text-align: center;
  font-size: 24rpx;
  color: #fff;
  background: rgba(0,0,0,0.5);
}
</style>

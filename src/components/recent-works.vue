<template>
  <div class="recent-works">
    <div class="headTitle">
      <span class="title">最近作品</span>
      <a @click="goAllWorks">MORE</a>
    </div>
    <div class="works">
      <ul v-for="(item,key) in works" :key="key">
        <li>
          <a class="works-item" @click="goIndexWorks(item)">
            <img :src="item.img" alt="">
            <div class="works-item-title">{{item.title}}</div>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        works:[
          {
            img:'../../static/images/1.jpeg',
            title: '一见钟情',
            id: '1'
          },
          {
            img:'../../static/images/2.jpeg',
            title: '这是标题2',
            id: '2'
          },
          {
            img:'../../static/images/3.jpg',
            title: '这是标题3',
            id: '3'
          }
        ]
      }
    },
    methods: {
      //跳转-全部作品页
      goAllWorks(){
        mpvue.navigateTo({
          url: `../../pages/all-works/main?title=最近作品`
        })
      },
      goIndexWorks(item){
        let url = item.url;
        let id = item.id;
        let title = item.title;
        mpvue.navigateTo({
          url: `../../pages/index-works/main?id=${id}&title=${title}url=${url}`
        })
      },
    },
  }
</script>

<style lang="wxss">
  .recent-works {
    margin-top: 20rpx;
    background: #fff;
  }
  .recent-works .headTitle{
    height: 60rpx;
    line-height: 60rpx;
    display: flex;
    justify-content: space-between;
  }
  .recent-works .headTitle .title{
    padding-left: 35rpx;
    position: relative;
    font-size: 32rpx;
    color: #060606;
  }
  .recent-works .headTitle .title::before{
    content: ' ';
    position: absolute;
    left: 0;
    top: 0;
    display: inline-block;
    width: 8rpx;
    height: 100%;
    background: #BC4B31;
  }
  .recent-works .headTitle a{
    margin-right: 10rpx;
    font-size: 26rpx;
    color: #8C8C8C;
  }
  .recent-works .works{
    padding: 0 10rpx;
  }
  .recent-works .works ul >li a{
    width: 100%;
    height: 340rpx;
    position: relative;
  }
  .recent-works .works ul >li a img{
    width: 100%;
    height: 330rpx;
  }
  .recent-works .works ul >li a .works-item-title{
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

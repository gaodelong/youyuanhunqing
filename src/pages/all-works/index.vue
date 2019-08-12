<template>
  <div class=" content_page">
    <ul v-for="(item,key) in works" :key="key">
      <li @click="goIndexWorks(item)">
          <img :src="item.img" alt="">
          <p class="works-item-title">{{item.title}}</p>
      </li>
    </ul>
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
          },
          {
            img:'../../static/images/2.jpeg',
            title: '这是标题4',
            id: '4'
          },
          {
            img:'../../static/images/1.jpeg',
            title: '这是标题5',
            id: '5'
          }
        ]
      }
    },
    computed: {},
    mounted(){
      console.log('>>>', this.$root.$mp.query);
      let title = this.$root.$mp.query.title;
      this.title = title;
      mpvue.setNavigationBarTitle({
        title: title
      })
    },
    methods: {
      //跳转作品详情
      goIndexWorks(item){
        let url = item.url;
        let id = item.id;
        let title = item.title;
        mpvue.navigateTo({
          url: `../../pages/index-works/main?id=${id}&title=${title}url=${url}`
        })
      }
    }
  }
</script>

<style scoped>
  .content_page ul{
    padding: 0 10rpx;
  }
  .content_page ul{
    margin-top: 10rpx;
  }
  .content_page ul li{
    margin-bottom: 20rpx;
    position: relative;
  }
  .content_page ul li img{
    width: 100%;
    height: 290rpx;
  }
  .content_page ul li p{
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

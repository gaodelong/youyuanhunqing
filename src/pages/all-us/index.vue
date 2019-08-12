<template>
  <div class=" content_page">
      <ul>
        <li v-for="(item,index) in allUs" :key="index" @click="goAboutUsDetail(item)">
          <img :src=item.url alt="">
          <p>{{item.title}}</p>
        </li>
      </ul>
  </div>
</template>

<script>

  export default {

    data() {
      return {
        allUs: [
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
  .content_page ul{
    padding: 0 10rpx;
  }
  .content_page ul{
    margin-top: 10rpx;
  }
  .content_page ul li{
    display: inline-block;
    vertical-align: top;
    width: 49%;
    margin-bottom: 20rpx;
  }
  .content_page ul li:nth-child(odd){
    margin-right: 1%;
  }
  .content_page ul li:nth-child(even){
    margin-left: 1%;
  }
  .content_page ul li img{
    width: 100%;
    height: 290rpx;
  }
  .content_page ul li p{
    color: #888888;
    background-color: #fff;
    font-size: 24rpx;
    text-align: center;
  }
</style>

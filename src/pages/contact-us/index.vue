<template>
  <div class=" content_page">
    <div class="banner">
      <img :src="bannerImg" alt="">
    </div>
    <div class="banner-title">
      <div class="banner-title-logo">
        <img :src="bannerTitleLogo" alt="">
      </div>
      <div class="banner-title-text">{{bannerTitle}}</div>
    </div>
    <div class="form">
      <van-cell clickable @click="clickCallPhone(phone1)" :title="phone1" value="点击拨打" icon="phone-o" class="redColor"/>
      <van-cell clickable @click="clickCallPhone(phone2)" :title="phone2" value="点击拨打" icon="phone-o" class="redColor"/>
      <van-cell clickable @click="clickMapLocation" :title="address" title-width="70%" value="地图导航" icon="location-o" class="redColor"/>

      <div class="btns">
        <button type="primary" class="submit-btn">
          <van-icon name="orders-o" size="20px"  style="vertical-align: middle"/>
          保存通讯录
        </button>
        <button type="primary" class="submit-btn" open-type="share">
          <van-icon name="share" size="20px"  style="vertical-align: middle"/>
          分享给好友
        </button>
      </div>
    </div>
    <!--拨打电话-->
    <van-action-sheet
      :show="phoneDrawer"
      :actions="sheetAcitons"
      @select="clickSheetAction"
      cancel-text="取消"
      @cancel="clickCancel"
    />
  </div>
</template>

<script>

  export default {

    data() {
      return {
        bannerImg: '../../static/images/2.jpeg',
        bannerTitle: '友缘文化婚庆策划',
        bannerTitleLogo: '../../static/images/2.jpeg',
        phone1:'0917-7756000',
        phone2:'15102923172',
        address: '陕西省宝鸡市凤翔县南指挥镇太南村',
        phoneDrawer: false,
        sheetAcitons: [
          {
            name: '0917-7756000'
          },
          {
            id: '1',
            name: '呼叫'
          }
        ],

      }
    },
    computed: {},
    mounted(){

    },
    methods: {
      //地图导航
      clickMapLocation(){
        mpvue.openLocation({
          latitude: 34.5288310000,
          longitude: 107.4030080000,
        })
      },
      clickSheetAction(event){
        if (event.mp.detail.name === '呼叫' && event.mp.detail.id === '1'){
          mpvue.makePhoneCall({
            phoneNumber: '0917-7756000'
          })
        }
        if (event.mp.detail.name === '呼叫' && event.mp.detail.id === '2') {
          mpvue.makePhoneCall({
            phoneNumber: '15102923172'
          })
        }
      },
      clickCallPhone(item){
        this.phoneDrawer = true;
        if (item === '15102923172'){
          this.sheetAcitons = [{name: '15102923172'},{id: '2',name: '呼叫'}]
        }else{
          this.sheetAcitons = [{name: '0917-7756000'},{id: '1',name: '呼叫'}]
        }
      },
      clickCancel(){
        this.phoneDrawer = false;
      }
    },
   //分享
    onShareAppMessage: function (res) {
      return{
        title:'友缘文化传媒',
        desc: '一站式婚礼私人定制',
      }
    }
  }
</script>

<style>
  .redColor .van-cell__value{
    color: red;
  }
</style>
<style scoped>
  .content_page {
    position: relative;
  }

  .content_page .form {
    /*margin: 60rpx 0;*/
  }
  .content_page .banner{
    z-index: 80;
  }
  .content_page .banner img {
    width: 100%;
    z-index: 88;
  }

  .banner-title {
    position: relative;
    display: flex;
    margin: 0 80rpx;
    background: #fff;
    padding: 20rpx;
    margin-top: -120rpx;
    box-shadow: 0px 2px 3px rgba(150,154,157,1);
    z-index: 100;
  }
  .banner-title .banner-title-logo img{
    width: 90rpx;
    height: 90rpx;
    border-radius: 90rpx;
  }
  .banner-title .banner-title-text{
    line-height: 90rpx;
    margin: 0 50rpx 0 90rpx;
    font-size: 36rpx;
    /*font-weight: bold;*/
    text-shadow: 0px 0px 0px rgba(0,0,0,1);
    color: #666666;
  }
  .btns{
    display: flex;
    margin-top: 20rpx;
  }
  .submit-btn {
    height: 90rpx;
    line-height: 90rpx;
    vertical-align: middle;
    margin: 20 rpx 15 rpx 0;
    background: #BC4B31;
  }

</style>

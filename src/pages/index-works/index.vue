<template>
  <div class="content">
    <h4>{{title}}</h4>
    <div class="head">
      <span class="date">{{date}}</span>
      <!--<a class="share">-->
        <!--<img :src="shareSrc" alt="">-->
        <!--<span>分享</span>-->
      <!--</a>-->
    </div>
    <!--视频-->
    <div class="video">
      <video :src="videoUrl" style="width: 100%"></video>
    </div>
    <!--文章-->
    <div class="article">
      <p v-html="computedArticle"></p>
    </div>
    <ul>
      <li v-for="(item,key) in personInfo" :key="key">
        <img :src="item.img" alt="">
        <p class="introduce-text">{{item.text}}</p>
      </li>
    </ul>
    <div class="bottom">
      <div class="left-buttons">
        <div class="lst">
          <img :src="eysSrc" alt=""  style="margin-top: 2px">
          <span class="eye-number">{{eyeNumber}}</span>
        </div>
        <div class="lst">
          <img :src="goodSrc" alt="">
          <span class="good-number">{{goodNumber}}</span>
        </div>
        <div class="lst">
          <a class="share" @click="clickShareSheet">
            <img :src="shareSrc" alt="">
            <span>分享</span>
          </a>
        </div>
      </div>
      <div class="right-comment">
        <div class="lst" @click="clickComment">
            <img :src="penSrc" alt="">
            <span>评论</span>
        </div>
      </div>
    </div>
    <!--评论弹窗-->
    <van-dialog
      use-slot
      title=" "
      :show="dialog"
      show-cancel-button
      confirm-button-open-type="getUserInfo"
      @close="onClose"
      @getuserinfo="getUserInfo"
    >
    <div class="comment-main">
      <div style="margin:0 auto;text-align: center">
        <van-rate :value="rateValue" @change="rateOnChange" />
      </div>
      <!--<p>评论内容:</p>-->
      <van-field
        :value="fieldValue"
        type="textarea"
        autosize
        placeholder="评论内容"
        :border="true"
      ></van-field>
    </div>
    </van-dialog>
    <!--分享sheet-->
    <van-action-sheet
      :show="shareDrawer"
      @select="clickSheetAction"
      cancel-text="取消"
      @cancel="clickCancel"
    >
      <action-sheet-item class="margin30">
        <button open-type="share">分享给好友</button>
      </action-sheet-item>
      <action-sheet-item class="margin30">
        <button>生成海报分享到朋友圈</button>
      </action-sheet-item>

    </van-action-sheet>
  </div>
</template>

<script>
  // import Dialog from '../../../static/vant/dialog/dialog';
  export default {

    data() {
      return {
        dialog: false,
        title: '',
        date: '2019-07-15',
        shareSrc: '../../static/images/share.png',
        eysSrc: '../../static/images/eye.png',
        eyeNumber: '10',
        goodSrc: '../../static/images/good.png',
        goodNullSrc: '../../static/images/good_null.png',
        goodNumber: '1',
        penSrc: '../../static/images/pen.png',
        personInfo:[
          {
            img: '../../static/images/1.jpeg',
            text: '张小敬'
          }
        ],
        //星值
        rateValue: 0,
        fieldValue: '',
        shareDrawer: false,
        sheetAcitons:[
          {
            id: '1',
            name: '分享给朋友'
          },
          {
            id: '2',
            name: '生成海报分享到朋友圈'
          }
        ],
        //视频url
        videoUrl: '',
        //文章
        article: ''
      }
    },

    computed:{
      computedArticle(){
        return this.article;
      }
    },
    created() {
    },
    mounted() {
      console.log('>>>', this.$root.$mp.query);
      let title = this.$root.$mp.query.title;
      this.title = title;
      mpvue.setNavigationBarTitle({
        title: title
      });
      //模拟视频路径
      if(this.$root.$mp.query.id === '1'){
        this.videoUrl = 'http://vfx.mtime.cn/Video/2019/02/04/mp4/190204084208765161.mp4';
        this.article = '生命的序号是成长的编排<br>或许忧愁在先<br>或许快了在后<br>但是请坚信我爱你一定在其中<br>而且一直坚守在幸福身旁';
      }
      else if (this.$root.$mp.query.id === '2'){
        this.videoUrl = 'http://vfx.mtime.cn/Video/2019/03/21/mp4/190321153853126488.mp4';
        this.article = '我没有华丽的语言<br>更不会表达自己真实的情感<br>但我有一颗永远倾向你的心<br>那是颗为你而跳动的红色的心'
      }else if (this.$root.$mp.query.id === '3') {
        this.videoUrl = 'http://vfx.mtime.cn/Video/2019/03/19/mp4/190319212559089721.mp4';
        this.article = '你可曾记得<br>我们肩并着肩,手挽着手,走过那一段艰难的旅程<br>我们眼望着眼,心连着心,共谱那一段爱的主题曲'
      }
    },
    methods:{
      clickSheetAction(event){

      },
      clickShareSheet(){
        this.shareDrawer = true;
      },
      clickCancel(){
        this.shareDrawer = false;
      },
      clickComment(){
        this.dialog = true;
      },
      getUserInfo(event){
        // console.log(event.mp.detail)
      },
      onClose(event) {
        if (event.mp.detail === 'confirm') {
          // 异步关闭弹窗
          setTimeout(() => {
            this.dialog=false
          }, 1000);
        } else {
          this.dialog=false
        }
      },
      //星值改变
      rateOnChange(event){
        // console.log(event.mp.detail);
      },

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

<style scoped>
  .content{
    margin:0 20rpx;
  }
  h4 {
    margin-top: 20rpx;
    margin-bottom: 15rpx;
    font-size: 34rpx;
    font-weight: bold;
  }
  .head{
    display: flex;
    line-height: 40rpx;
  }
  .head .date{
    font-size: 26rpx;
     color: #999999;
  }
  .head .share{
    margin-left: 15rpx;
  }
  .head .share img{
    width: 40rpx;
    height: 34rpx;
  }
  .head .share >span{
    vertical-align: top;
    font-size: 24rpx;
    color: #999999;
  }
  .content >ul{
    margin-top: 10rpx;
  }
  .content >ul >li img{
    width: 100%;
    /*height: 400rpx;*/
  }
  .content >ul >li .introduce-text{
    text-align: center;
    margin: 0 auto;
    font-size: 45rpx;
    color: #666666;
  }
  .bottom{
    margin: 40rpx 0;
    display: flex;
    justify-content: space-between;
  }
  .bottom .left-buttons{
    display: flex;
  }
  .bottom .left-buttons .lst{
    align-items: center;
    margin-right: 20rpx;
  }
  .bottom .left-buttons img,.bottom .right-comment img{
    width: 32rpx;
    height: 32rpx;
  }
  .bottom .left-buttons span, .bottom .left-buttons .lst .share span,.bottom .right-comment span{
    display: inline-block;
    vertical-align: top;
    font-size: 26rpx;
    color: #707070;
  }
  .comment-main{
    margin: 0 15rpx;
    font-size: 24rpx;
  }
  .margin30{
    margin: 20rpx 60rpx;
    padding: 0;
  }
  .article p{
    font-size: 30rpx;
    color: #000;
  }
</style>

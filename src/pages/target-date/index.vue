<template>
  <div class="container content_page">
    <div class="banner">
      <img :src="bannerImg" alt="">
    </div>
    <div class="form">
      <p class="text">{{text}}</p>
      <van-cell-group>
        <van-field
          :value="name"
          required
          clearable
          label="姓名"
          placeholder="请输入姓名"
        />
        <van-field
          :value="phone"
          type="number"
          label="电话"
          placeholder="请输入电话"
          required
        />
        <van-field
          :value="maryDate"
          label="婚期"
          placeholder="请选择日期"
          required
          readonly
          @click="maryDateFocus"
        />
        <van-field
          :value="address"
          label="酒店"
          placeholder="请输入地址"
          required
        />
        <van-field
          type="textarea"
          :value="remark"
          label="备注"
          placeholder="请输入备注信息"
        />
      </van-cell-group>
      <button type="primary" class="submit-btn">提交</button>
    </div>
    <van-action-sheet :show="isShowPicker">
      <van-datetime-picker
        type="date"
        @cancel="cancel"
        @confirm="confirm"
      />
    </van-action-sheet>
  </div>
</template>

<script>

export default {

  data(){
    return{
      bannerImg: '../../static/images/2.jpeg',
      text: '婚期示例(2019.10.01)  酒店请写楼层',
      name: '',
      phone: '',
      isShowPicker: false,
      date:new Date(),
      maryDate: '',
      address: '',
      remark: ''
    }
  },
  computed:{

  },
  methods: {
    onInput(event) {
      this.setData({
        date: event.detail
      });
    },
    maryDateFocus(){
      this.isShowPicker = true;
    },
    confirm(value) {
      console.log(new Date(value.mp.detail));
      let date = new Date(value.mp.detail);
      let year =  date.getFullYear();
      let seperator1 = ".";
      let month = date.getMonth() + 1;
      let strDate = date.getDate();
      if (month >= 1 && month <= 9) {
        month = "0" + month;
      }
      if (strDate >= 1 && strDate <= 9) {
        strDate = "0" + strDate;
      }
      this.date =
        year +
        seperator1 +
        month +
        seperator1 +
        strDate;

      this.maryDate = this.date;
      this.cancel();
    },
    cancel(){
      this.isShowPicker = false
    },
  }
}
</script>

<style scoped>
.content_page{
}
.content_page .form{
  /*margin: 60rpx 0;*/
}
.content_page .banner img{
    width: 100%;
}
.content_page .form .text{
  margin-left: 20rpx;
  margin-bottom: 15rpx;
  font-size: 24rpx;
  color: #7F7F7F;
}
  .submit-btn{
    margin: 20rpx 15rpx 0;
    background: #BC4B31;
  }
</style>

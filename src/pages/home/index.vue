<template>
  <div class="indexContainer">
    <img class="indeximg"  :src="userInfo.avatarUrl" alt="">
    <!-- <Button class="btn" open-type="getUserInfo" @getuserinfo="getUserInfo">开始</Button> -->
     <Button class="btn"  @tap="change">开始</Button>
    <p class="userName">hello  {{userInfo.nickName}}</p>
    <div class="start">
      <p>开始专属于你的心情记录</p>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      isShow:false,
      userInfo:{},
      motto: 'Hello miniprograme',
    }
  },

  components: {
    card
  },
beforeMount(){
      this.handleGetUserInfo(),
      console.log("jianglai")
    },
  methods: {
    handleGetUserInfo(){
     wx.getUserInfo({
       success : (data)=> {
         console.log(data);
         this.userInfo = data.userInfo;
       },
       fail : ()=>{
         console.log('获取失败');
       }
     })
    },
  //   getUserInfo (data) {
  //     if(data.mp.detail.rawData) {
  //       this.handleGetUserInfo();
  //       console.log("经过了打印")
  //     }
  //   }
  // },
  change () {
      wx.navigateTo({
        url:('/pages/mood/main')
      })
      console.log('dianji')
  }
  },
  created () {
    // let app = getApp()
   
  }
}
</script>

<style scoped>
 page {
  background-image: url('http://img2.imgtn.bdimg.com/it/u=3316664839,999263507&fm=26&gp=0.jpg')
  
}
.indexContainer {
  display: flex;
  flex-direction: column;
  align-items: center; 
  background-image: url('http://img2.imgtn.bdimg.com/it/u=3316664839,999263507&fm=26&gp=0.jpg') 
   /* 使样式居中 */
}
.indeximg {
  width:200rpx;
  height:200rpx;
  border-radius: 100rpx;
  margin: 180rpx 0;
}
.userName {
font-size: 40rpx;

margin: 50rpx 0;
}
.start{
width: 280rpx;
height: 80rpx;
border: 1rpx solid #eeeeee;
font-size: 24rpx;
line-height: 80rpx;
text-align: center;
margin: 50rpx 0;
}
.btn{
width: 150rpx;
height: 150rpx;
border-radius:200rpx;
margin :20rpx;
line-height:150rpx;
text-align:center;
font-size:28rpx;
font-weight: bold;
}
</style>

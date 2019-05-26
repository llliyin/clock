<template>
  <div class="indexContainer">
    <view  class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <!-- <Button class="btn" open-type="getUserInfo" @getuserinfo="getUserInfo">开始</Button> -->
     <Button class="btn"  @tap="change">开始</Button>
    <p class="userName">hello  {{userInfo.nickName}}</p><span><open-data type="userNickName"></open-data></span>
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
        userInfo: { 
        nickName: '',
        avatarUrl: '',
        
      }
    }
  },

  components: {
    card
  },
beforeMount(){
      // this.handleGetUserInfo(),
      // console.log("jianglai")
    },
  methods: {
    // handleGetUserInfo(){
    //  wx.getUserInfo({
    //    success : (data)=> {
    //      console.log(data);
    //      this.userInfo = data.userInfo;
    //    },
    //    fail : ()=>{
    //      console.log('获取失败');
    //    }
    //  })
    // },
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
      // wx.cloud.callFunction ({name:'mymood'}).then (res => {console.log (res)})
      // const db = wx.cloud.database({env:'clockdata-3a158b'})
      // db.collection('mymood').add({ss
      //   data : {
      //     date: '2019.4.15',
      //     mood:'很满足',
      //     note:'今天上学到了很多东西',
      //     persentage:"30",
      //     picture:'cloud://clockdata-3a158b.636c-clockdata-3a158b/angry.png'

      //   },success(res) {
      //     console.log(res)
      //   }
      // })

  }
}
</script>

<style scoped>
 page {
  background-image: url('http://img2.imgtn.bdimg.com/it/u=3316664839,999263507&fm=26&gp=0.jpg');
  background-repeat: no-repeat;
  
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
width: 200rpx;
height: 200rpx;
border-radius:200rpx;
margin :20rpx;
line-height:150rpx;
line-height: 200rpx;
text-align:center;
font-size:28rpx;
font-weight: bold;
}
.userinfo-avatar {
overflow:hidden;
display: block;
width: 160rpx;
height: 160rpx;
margin: 180rpx 0;
border-radius: 50%;
border: 2px solid #fff;
box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}
.userinfo {
position: relative;
width: 750rpx;
height: 320rpx;
color: #666;
display: flex;
flex-direction: column;
align-items: center;
}
</style>

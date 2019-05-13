<template>
  <div class="indexContainer">
    <view class="userinfo">
    <view  class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>
    <div class="userinfo2">
     <p>
       新一天，新心情
     </p>
    </div>
    <i-panel title="今天天气不错，你的心情是什么样子的呢">
    <i-grid class="no-border">
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image @tap="chooseHappy"  src="/static/images/happy1.png" />
        </i-grid-icon>
        <i-grid-label>开心</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image @tap="choosenoexPression" src="/static/images/noexPression.png" />
        </i-grid-icon>
        <i-grid-label>一般般</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image @tap="choosesad" src="/static/images/sad.png" />
        </i-grid-icon>
        <i-grid-label>伤心</i-grid-label>
    </i-grid-item >
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image @tap="chooseangry" src="/static/images/angry.png" />
        </i-grid-icon>
        <i-grid-label>愤怒</i-grid-label>
    </i-grid-item>
        <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image @tap="chooselike" src="/static/images/like.png" />
        </i-grid-icon>
        <i-grid-label>喜欢</i-grid-label>
    </i-grid-item>
</i-grid>
    </i-panel>
      <i-panel hide-border=“true” i-class="no-border">
    <view style="padding: 10px;"> </view>
    </i-panel>

    <view class="percentage" style="padding: 10px">
      <p calss="word">
        请选择心情程度百分比
      </p>
    </view>

    <i-panel hide-border=“true”>
    <view style="padding: 8px;"> </view>
    </i-panel>
     <i-card title="心晴进度"  extra="日期" :thumb ="url" >
    <view slot="content"> 
    <i-progress :percent="persentage"  stroke-width:30px>
    </i-progress>
     
    </view>
    <view slot="footer"> <input @input="noteInput" placeholder="请记录心情事件"  />
  <div class="content">
  
    <text class="text">{{note}}</text>
     </div>
    
    </view>
    
    
   </i-card>
   <view  class="btn">
     <button  type="default" @tap="addPersentage" size="mini" plain="true" >增加</button>
   </view>
   
  <i-button class="ibutton" @tap="addData" type="primary" shape="circle" size="small">{{submit}}</i-button>
  

  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      logs:[ ],
      submit:"提交",
      date:'',
      mood: 'bucuo',
      note :"",
      persentage :0,
      picture: 'http://mpvue.com/assets/logo.png',
      motto: 'Hello miniprograme',
      url:'/static/images/noexPression.png',
     userInfo: { 
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png',
        
      }
    }
  },

  components: {
    card
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    },
    chooseHappy() {
      this.url="/static/images/happy1.png"
    },
    choosenoexPression() {
      this.url="/static/images/noexPression.png"
    },
    choosesad() {
      this.url="/static/images/sad.png"
    },
    chooseangry() {
      this.url="/static/images/angry.png"
    },
    chooselike() {
      this.url="/static/images/like.png"
    },
    noteInput (e) {
      this.note = e.mp.detail.value
      //将用户输入的文本传到note的值中
      // this.setData({
      // note: e.detail.value
    // })
    // console.log(e.mp.detail.value)
    // console.log (note)
    },
    addPersentage(){
      if(this.persentage==100){
       this.persentage=0
      }
      this.persentage = this.persentage+10
      
    },
    addData () {
      var myDate = new Date();
      var time = myDate.toLocaleDateString();     //获取当前日期
      const db = wx.cloud.database({env:'clockdata-3a158b'})
      db.collection('mymood').add({
        data : {
          
          date:time,
          mood:this.mood,
          note:this.note,
          persentage:this.persentage,
          picture:this.url

        }
      })
      this.submit="提交成功"
    }
  },

  created () {
    // let app = getApp()
    // let logs
    // if (mpvuePlatform === 'my') {
    //   logs = mpvue.getStorageSync({key: 'logs'}).data || []
    // } else {
    //   logs = mpvue.getStorageSync('logs') || []
    // }
    // this.logs = logs.map(log => formatTime(new Date(log)))
    //  logs = mpvue.getStorageSync({key: 'logs'}).data || []
    // let logs
    // logs = mpvue.getStorageSync({key: 'logs'}).data || []
    // console.log(logs)
  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
.content{
  border:1px gainsboro solid;
  border-radius: 4px;
}
.userinfo2 {
position: relative;
width: 750rpx;
height: 100rpx;
color: #666;
display: flex;
flex-direction: column;
align-items: center;
margin: 10rpx;
}
.ibutton{
  margin: 50rpx;
  color: antiquewhite;
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
.percentage{
  text-align: center;
  color: #666;
}
.start{
position: relative;
width: 280rpx;
height: 80rpx;
border: 1rpx solid #eeeeee;
font-size: 24rpx;
line-height: 80rpx;
text-align: center;
margin: 50rpx 0; 
}
.indexContainer{
  display: flex;
  flex-direction: column;
}
.btn{
  text-align:center;
  margin: 30rpx;
  border-color: #eeeeee
  
}
.word{
  font-size: 40rpx;
  color: #666;
}
 .text {
   margin: 20;
   font-size: 24rpx;
   word-spacing: 10rpx;
 }
.userinfo-avatar {
overflow:hidden;
display: block;
width: 160rpx;
height: 160rpx;
margin: 20rpx;
margin-top: 50rpx;
border-radius: 50%;
border: 2px solid #fff;
box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}
</style>
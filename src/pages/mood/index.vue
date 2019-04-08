<template>
  <div class="indexContainer">
    <view class="userinfo">
    <view class="userinfo-avatar">
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
            <image src="/static/images/happy.png" />
        </i-grid-icon>
        <i-grid-label>开心</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/images/noexPression.png" />
        </i-grid-icon>
        <i-grid-label>一般般</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/images/sad.png" />
        </i-grid-icon>
        <i-grid-label>伤心</i-grid-label>
    </i-grid-item >
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/images/angry.png" />
        </i-grid-icon>
        <i-grid-label>愤怒</i-grid-label>
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
     <i-card title="心晴进度"  :thumb ="url" >
    <view slot="content"> 
    <i-progress percent="25" stroke-width:30px>
    </i-progress>
    </view>
    <view slot="footer">随便写点啥</view>
   </i-card>
  <i-button class="ibutton" type="primary" shape="circle" size="small">增加</i-button>

  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
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
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
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
.word{
  font-size: 40rpx;
  color: #666;
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
<template>
  <div>
    <view class="userinfo">
    <view class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>
    <i-panel hide-border=“true”>
    <view style="padding: 15px;">今天天气不错，你的心情呢</view>
    </i-panel>
    <i-panel hide-border=“true”>
    <view style="padding: 15px;">    </view>
    </i-panel>
    <i-panel title="请选择你的心情">
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
 <i-panel hide-border=“true”>
    <view style="padding: 15px;">请选择心情百分比</view>
  </i-panel>
    <i-panel hide-border=“true”>
    <view style="padding: 8px;"> </view>
    </i-panel>
   <i-card title="心晴进度" thumb="/static/images/noexPression.png">
    <view slot="content"> 
    <i-progress percent="25" stroke-width:30px>
    </i-progress>
    </view>
    <view slot="footer">  </view>
   </i-card>
   <i-row>
    <i-col span="8" i-class="col-class">shrm</i-col>
    <i-col span="8" i-class="col-class">ugim</i-col>
    </i-row>  

    
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello miniprograme',
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
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
.userinfo {
position: relative;
width: 750rpx;
height: 320rpx;
color: #666;
display: flex;
flex-direction: column;
align-items: center;
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
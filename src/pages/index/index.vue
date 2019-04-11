<template>
  <div @click="clickHandle">
    <view v-for="item in mood" :key="item">
      <i-card  title="心晴进度" extra="额外内容" thumb="/static/images/sad.png">
       <view slot="content"> 
       <i-progress percent="20" stroke-width:30px>
       </i-progress>
      </view>
        <view slot="footer">脚本内容</view>
     </i-card>
    </view>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello miniprograme',
       mood : [],
      userInfo: {
      nickName: 'mpvue',
      avatarUrl: 'http://mpvue.com/assets/logo.png',
      bianliang:['shuzi','jiegou'],
      
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
    const db = wx.cloud.database({env:'clockdata-3a158b'})
    db.collection('mymood').get().then(
      res => {
        console.log(res.data)
        this.mood = res.data
       
      }
    )
//      wx.cloud.callFunction({ name: 'mymood' }).then(
//      res => {console.log(res)}
// )

  }
}
</script>

<style scoped>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 150px;
}

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  border: 1px solid #ccc;
}
.all{
  width:7.5rem;
  height:1rem;
  background-color:blue;
}
.all:after{
  display:block;
  content:'';
  clear:both;
}
.left{
  float:left;
  width:3rem;
  height:1rem;
  background-color:red;
}

.right{
  float:left;
  width:4.5rem;
  height:1rem;
  background-color:green;
}
</style>

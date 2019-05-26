<template>
  <div class="indexContainer">
    <!-- <div class="head">
      <p>联系作者</p>
    </div> -->
    <div class="pannal">
        联系作者
  </div >
  <div class="card">
  <i-card title="欢迎来稿" extra="越多越好" thumb="/static/images/huaduo.png"  full="true">
    <view slot="content">
      <div class="img"><img src="/static/images/code.png" alt="二维码"></div>
    </view>
    <view slot="footer">请备注：小程序</view>
</i-card>
 <Button @click="re" class="btn" >返回</Button>
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
    
  change () {
      wx.navigateTo({
        url:('/pages/mood/main')
      })
     
  },
  re () {
   wx.switchTab({
  url: '/pages/logs/main'
})
      
  }
  },
  
}
</script>

<style scoped>
p{
  font-size: 18px;
  font-style: normal；
 
}
.btn{
  margin-top: 30px;
  text-align: center;
  width: 80px;
  height: 40px;
}

.head{
  margin-top:30px;
  margin-bottom:20px;
}
.pannal{
  text-align: center;
  font-size: 20px;
  margin-top:50px;
  margin-bottom:5px;
}
.card{
  margin-top:60px;
}
 
.indexContainer {
  text-align: center;
  display: flex;
  flex-direction: column;
 color: gray
   /* 使样式居中 */
}
.img{
  display: inline-block; 
  

}

</style>

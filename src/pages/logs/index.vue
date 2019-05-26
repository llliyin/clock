<template>
  <div>
    <div>
      <view class="user">
      <open-data class="userAvatar" type="userAvatarUrl" ></open-data>
      
      
        <open-data type="userNickName" class="userNickName"></open-data>
     
      </view>
    </div>
    <div >
      <swiper class="swiper" indicator-dots="true" indicator-color="white" indictor-active-color="green" autoplay="true">
      
        <swiper-item>
          <image src="/static/images/1.jpg"  class="swiperImage"></image>
        </swiper-item>
        <swiper-item>
          <image class="swiperImage" src="/static/images/2.jpg"  ></image>
        </swiper-item>
        <swiper-item>
          <image class="swiperImage" src="/static/images/3.jpg"  ></image>
        </swiper-item>
        <swiper-item>
          <image class="swiperImage" src="/static/images/4.jpg"  ></image>
        </swiper-item>
        <swiper-item>
          <image src="/static/images/6.jpg"  ></image>
        </swiper-item>
        <swiper-item>
          <image class="swiperImage" src="/static/images/7.jpg"  ></image>
        </swiper-item>
      
    </swiper>
    <i-cell-group>
    <i-cell title="我要提意见" is-link url="../suggestions/main"></i-cell>
    <i-cell title="我希望的新功能" is-link url="../suggestions/main"></i-cell>
    <i-cell title="联系作者" is-link url="../suggestions/main" ></i-cell>
    <!-- <i-cell title="开关">
        <switch slot="footer" checked />
    </i-cell> -->
</i-cell-group>
    </div>

  </div>
</template>

<script>
import { formatTime } from '@/utils/index'
import card from '@/components/card'

export default {
  components: {
    card
  },

  data () {
    return {
      picture:[],
      logs: [],
      imgUrls: [
        'http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/newsPicture/05558951-de60-49fb-b674-dd906c8897a6',
        'http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/coursePicture/0fbcfdf7-0040-4692-8f84-78bb21f3395d',
        'http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/management-school-picture/7683b32e-4e44-4b2f-9c03-c21f34320870'
      ]
    }
  },
  methods:{
    

  },

  created () {
    
  }
}
</script>

<style>
.userAvatar{
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
.log-list {
  display: flex;
  flex-direction: column;
  padding: 40rpx;
}
.swiper {
  text-align:center;
  margin-top: 30rpx;
}
.user{
  display: flex;
  flex-direction: row;
  text-align: center;
  vertical-align: center;
  align-items: center;
  font-size: 35rpx;
  color: dimgray;
}
.log-item {
  margin: 10rpx;
}
.swiperImage{
  width: 80%;
  height: 100%
}
</style>

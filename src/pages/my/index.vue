<template>
    <div>
        <view class="header">
            <view class="user-avatar-bg" v-if="userInfo.avatarUrl">
                <image class="pic" :src="userInfo.avatarUrl" />
            </view>
            <view class="user-head" v-else>
                <image @tap="getUserInfo" class="pic" :src="userInfo.avatarUrl || '/static/images/user.png'" />
            </view>
            <text class="name">{{ userInfo.nickName }}</text>
            <button v-if="!userInfo.nickName" class="weui-btn mini-btn" size="mini" type="default" open-type="getUserInfo" @getuserinfo="getUserInfo">授权获取信息</button>
            <!-- <button open-type="openSetting">打开授权设置页</button> -->
        </view>
        <navigator class="list">
            <text>我的足迹</text>
            <text>></text>
        </navigator>
        <navigator url="/pages/raiders/main" class="list">
            <text>我的攻略</text>
            <text>></text>
        </navigator>
        <navigator url="/pages/upload/main" class="list">
            <text>上传图片</text>
            <text>></text>
        </navigator>
        <navigator url="/pages/feedback/main" class="list">
            <text>意见反馈</text>
            <text>></text>
        </navigator>
        <navigator url="/pages/contact/main" class="list">
            <text>联系我们</text>
            <text>></text>
        </navigator>
    </div>
</template>

<script>
export default {
    data() {
    return {
      userInfo: {}
    }
  },
  onLoad() {
    if(wx.getStorageSync('userInfo')){
      this.userInfo = wx.getStorageSync('userInfo')
    }
  },
  methods: {
    getUserInfo() {
      // 调用登录接口
      wx.login({
        success: (res) => {
          wx.getUserInfo({
            success: res => {
              this.userInfo = res.userInfo
              wx.setStorageSync('userInfo',res.userInfo)
            }
          })
        }
      })
    },
    
  }
}
</script>
<style lang="scss">
    .header{
        width: 100%;
        height: 200px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background: #57bc90;
        margin-bottom: 10px;
        .pic{
            width: 40px;
            height: 40px;
            border-radius: 20px;
            border: 5px solid #fff;
        }
        .name{
            color:#fff;
            font-size: 16px;
        }
    }
    .list{
        height: 50px;
        border-bottom:1px solid #57bc90;
        color: #999;
        padding: 0 20px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 16px;
        margin-bottom: 10px;
    }
</style>


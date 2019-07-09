<template>
    <div>
        <view class="photo">
            <navigator
              url="#"
              open-type="navigate"
              hover-class="none" v-for="item in imgList" :key="item.id" class="photo-img">
                <img :src="item.imgUrl" alt="">
            </navigator>
        </view>
    </div>
</template>

<script>
export default {
    data() {
        return {
            imgList: [
                {id:1001,imgUrl:'../../static/images/banner01.jpg'},
                {id:1002,imgUrl:'../../static/images/banner02.jpg'},
                {id:1003,imgUrl:'../../static/images/banner03.jpg'},
                {id:1004,imgUrl:'https://images.unsplash.com/photo-1551446591-142875a901a1?w=640'},
                {id:1005,imgUrl:'../../static/images/banner01.jpg'},
                {id:1006,imgUrl:'../../static/images/banner02.jpg'},
                {id:1007,imgUrl:'../../static/images/banner03.jpg'},
                {id:1008,imgUrl:'https://images.unsplash.com/photo-1551446591-142875a901a1?w=640'},
                {id:1009,imgUrl:'../../static/images/banner01.jpg'},
                {id:1010,imgUrl:'../../static/images/banner02.jpg'},
                {id:1011,imgUrl:'../../static/images/banner03.jpg'},
                {id:1012,imgUrl:'https://images.unsplash.com/photo-1551446591-142875a901a1?w=640'},
                {id:1013,imgUrl:'../../static/images/banner04.jpg'},
                {id:1014,imgUrl:'../../static/images/banner02.jpg'},
                {id:1015,imgUrl:'../../static/images/banner01.jpg'},
                {id:1016,imgUrl:'https://images.unsplash.com/photo-1551446591-142875a901a1?w=640'}
            ],
        }
    },

//  // 下拉刷新
//   onPullDownRefresh: function () {
//     // 显示顶部刷新图标
//     wx.showNavigationBarLoading();
//     var that = this;
//     wx.request({
//     //   url: 'https://xxx/?page=0',
//       method: "GET",
//       header: {
//         'content-type': 'application/text'
//       },
//       success: function (res) {
//         that.setData({
//           moment: res.data.data
//         });
//         // 隐藏导航栏加载框
//         wx.hideNavigationBarLoading();
//         // 停止下拉动作
//         wx.stopPullDownRefresh();
//       }
//     })
//   },

//     /**
//    * 页面上拉触底事件的处理函数
//    */
//   onReachBottom: function () {
//     var that = this;
//     // 显示加载图标
//     wx.showLoading({
//       title: '玩命加载中',
//     })
//     // 页数+1
//     page = page + 1;
//     wx.request({
//       url: 'https://xxx/?page=' + page,
//       method: "GET",
//       // 请求头部
//       header: {
//         'content-type': 'application/text'
//       },
//       success: function (res) {
//         // 回调函数
//         var moment_list = that.data.moment;
//         const oldData = that.data.moment;
//         that.setData({
//            moment:oldData.concat(res.data.data)
//         })
//         // 隐藏加载框
//         wx.hideLoading();
//       }
//     })
 
//   }
}
</script>

<style lang="scss">
    .photo{
        width: 100%;
        padding-left: 5px;
        .photo-img{
            width: 45%;
            height: 100px;
            display: block;
            float: left;
            margin: 10px 0 0 10px;
            img{
             width: 100%;
            height: 100%;
            }
        }
        
    }
</style>

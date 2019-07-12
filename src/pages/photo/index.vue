<template>
    <div>
        <view class="photo">
            <view v-if="list.length==0" class="photo-tips">暂无图片</view>
            <view v-else>
                <navigator
              url="#"
              open-type="navigate"
              hover-class="none" v-for="item in imgList" :key="item.id" class="photo-img">
                <img :src="item.imgUrl" alt="">
            </navigator>
                <navigator
              url="#"
              open-type="navigate"
              hover-class="none" v-for="(item, index) in list" :key="index" class="photo-img">
                <img :src="item.filePath" alt="">
            </navigator>
            </view>
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
            list:[]
        }
    },
    onLoad() {
        const that=this
        wx.getSavedFileList({
        success (res) {
          that.list=res.fileList
        }
      })
    }
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
            border: 1px solid #f7f8f9;
            img{
             width: 100%;
            height: 100%;
            }
        }
        &-tips{
            text-align: center;
            margin: 20px 0;
            color: #666;
        }
    }
</style>

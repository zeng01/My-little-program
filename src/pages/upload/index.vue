<template>
    <view>
        <view class="upload-title">上传图片</view>
        <view @click="upload" class="upload-image">
            <image src="../../static/images/upload.jpg" class="upload-image-img">
            </image>
        </view>
    </view>
</template>

<script>
export default {
    methods: {
        upload(){
                  wx.chooseImage({
                    success: function(res) {
                        const tempFilePaths = res.tempFilePaths
                        wx.saveFile({
                        tempFilePath: tempFilePaths[0],
                        success (res) {
                            const savedFilePath = res.savedFilePath
                            console.log(res);
                            wx.showToast({
                                title: '上传成功', 
                                icon: 'success', 
                                duration: 2000, 
                                mask: true, 
                                success: res => {
                                    setTimeout(() => {
                                        wx.switchTab({
                                            url: '/pages/photo/main'
                                        })
                                    }, 2000);
                                }
                            });
                        }
                        })
                    }
                })
        }
    },
}
</script>

<style lang="scss">
    .upload-title{
        height:30px;
        padding: 10px;
        font-size: 16px;
        color: #fff;
        background: #57bc90;
        margin-top: 10px;
    }

    .upload-image{
        margin: 10px;
        border: 1px solid #ddd;
        text-align: center;
        &-img{
            width:60px;
            height: 60px;
            margin: 20px 0;
        }
    }
</style>

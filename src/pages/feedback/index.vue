<template>
    <view>
        <view class="header">意见反馈</view>
        <view class="from">
            <form @submit="bindFormSubmit">
                <textarea placeholder="您的宝贵意见" name="textarea" class="feedback"/>
                <button form-type="submit"> 提交 </button>
            </form>
        </view>        
    </view>
</template>

<script>
export default {
    data: {

    },
    methods: {
        bindFormSubmit: function(e) {
            if(e.target.value.textarea!=""){
                wx.showToast({
                title: '感谢您的反馈!', //提示的内容,
                icon: 'success', //图标,
                duration: 2000, //延迟时间,
                mask: true, //显示透明蒙层，防止触摸穿透,
                success: res => {
                    setTimeout(()=>{
                        wx.navigateBack({
                        delta: 1 //返回的页面数，如果 delta 大于现有页面数，则返回到首页,
                    });
                    },1000)
                }
                });
            }
        }
    },
}
</script>

<style lang="scss">
    .header{
        height:30px;
        margin: 20px 0;
        text-align: center;
        line-height: 30px;
        font-size: 18px;
    }
    .from{
        width: 100%;
        height: 200px;
        padding: 10px;
        box-sizing: border-box;
        .feedback{
            height: 100%;
            width: 100%;
            border: 1px solid #ccc;
            margin-bottom: 20px;
            font-size: 14px;
            padding:10px;
            box-sizing: border-box;
            color: #666;
        }
    }
</style>

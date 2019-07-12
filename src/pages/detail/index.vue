<template>
    <div>
        <view class="title">{{detail.title}}</view>
        <view class="picview-other">   
            <span class="po-name">作者：{{detail.author}}</span>
            <span class="po-view">浏览量：{{detail.view}}</span>
            <span class="po-date">日期：{{detail.date}}</span>
        </view>
        <view class="txt">
            <img :src="detail.imgUrl" alt="" class="pic">
            <view class="text">{{detail.text}}</view>
        </view>
        <view class="like">
            <view class="zan" @click="like">
                点赞(<text class="number">{{num}}</text>)
            </view>
        </view>
        <view class="comment">
            <button v-if="!userInfo.nickName" class="weui-btn mini-btn comment-logo" size="mini" type="default" open-type="getUserInfo" @getuserinfo="getUserInfo">登录后评论</button>
            <form @submit="commentSubmit" v-else>
                  <textarea placeholder="请输入评论" auto-height="true" name="textarea" class="comment-text" :value="form_info" />
                  <button form-type="submit" class="comment-btn">提交</button>
            </form>
            <view class="comment-title">评论</view>
            <view class="comment-list" v-if="commentList.length==0">
                <text class="no-comment">暂无评论</text>
            </view>
            <view v-else>
            <view class="comment-list border-bottom" v-for="(item, index) in commentList" :key="index">
                <text class="comment-list-name">{{userInfo.nickName}}</text>
                <text class="comment-list-text">{{item}}</text>
            </view>
            </view>
        </view>
        <!-- 回到顶部 -->
        <view @click="goToTop" class="to-top" v-show="isShowGoToTop">
            <span class="to-top-text">顶部</span>
        </view>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isShowGoToTop: false, // 是否显示回来顶部
            num:0,
            detail:{
                    id:1001,
                    imgUrl:'../../static/images/banner01.jpg',
                    view:23,
                    author:"admin",
                    date:2019-4-16,
                    title:'元阳，哈尼梯田的故乡',
                    text:"我们的行程从 伊兹密尔 出发到 塞尔丘克 、 博德鲁姆 、 代尼兹利 、 费特希耶 、 安塔利亚 、 卡帕多奇亚 ，最后从 内夫谢希尔 还车，全程主要是内陆高速、海滨公路、山区公路、内陆公路，路况非常好，基本都是双向两车道，全程柏油路。海滨和山区弯路多，相对曲折，天黑以后没有路灯，路况不熟悉尽量不要走夜路。我们走了两个小时D400夜路，瞪得10只眼珠+镜片都快掉下来了     A、高速国道公路路况：车速飞快，开到150后面的车还是会呼啸超过，完全忽视限速和监控。国道和公路是开放式的，高速行驶时，突然横穿马路的当地大叔大婶会把全车人吓傻，所以进村还是50以下吧。从 伊兹密尔 到 阿拉恰特 、 博德鲁姆 走了高速路，车很少路况不错，高速费很便宜，四次收费TRY14。土国的高速公路没有人工收费，高速路口有HGS和OGS 通道 标示，在AVIS租车时被告知走高速要使用HGS 通道 ，车辆通过时会显示扣费金额，还车时租车公司会从押金里一并扣减，完全不用操心。"
            },
            commentList:[],
            form_info:"",
            userInfo:""
        }
    },
    onLoad() {
        if(wx.getStorageSync('userInfo')){
            this.userInfo = wx.getStorageSync('userInfo')
        }
    },
    onPageScroll (e) {
        if (e.scrollTop > 80) {
        if (this.isShowGoToTop) return
        this.isShowGoToTop = true
        } else {
        if (!this.isShowGoToTop) return
        this.isShowGoToTop = false
        }
    },
    methods: {
        goToTop () {
            wx.pageScrollTo({
                scrollTop: 0,
                duration: 300
            })
        },
        like(){
            this.num++
        },
        commentSubmit(e){
            if(e.target.value.textarea!=""){
                wx.showToast({
                title: '评论成功！', //提示的内容,
                icon: 'success', //图标,
                duration: 1000, //延迟时间,
                mask: true, //显示透明蒙层，防止触摸穿透,
                success: res => {
                    this.commentList.push(e.target.value.textarea)  
                    this.setData({
                        form_info:""
                    })                
                }
                });
            }
        },
        commentLogo(){
            console.log(111);
            
            wx.navigateTo({ url: '/pages/my/main' });
        },
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
    }
        
    },
}
</script>

<style lang="scss">
    .title{
        height: 60px;
        line-height: 60px;
        color: #77c9d4;
        font-size: 18px;
        text-align: center;
    }
    .picview-other{
        height: 40px;
        line-height: 40px;
        font-size: 14px;
        text-align: center;
        .po-view{
            margin: 0 20px;
        }
    }
    .txt{
        padding: 10px;
        .pic{
            width: 100%;
        }
        .text{
            margin: 10px 0;
            font-size: 14px;
        }
    }
    .like{
        height: 40px;
        font-size: 20px;
        font-weight: 700;
        display: flex;
        align-items: center;
        justify-content: center;
        .zan{
            width: 100px;
            height: 40px;
            border-radius: 15px;
            border: 1px solid #d45;
            text-align: center;
            line-height: 40px;
        }
        .number{
            color:#d45;
        }
    }
    .comment{
        padding: 10px;
        &-logo{
            width: 120px;
            text-align: center;
            position:absolute;
            left: 50%;
            margin-left: -60px;
        }
        &-title{
            height: 30px;
            background: #ddd;
            color: #666;
            font-size: 14px;
            line-height: 30px;
            margin: 50px 0 10px;
        }
        &-text{
            height: 40px !important;
            border: 1px solid #ccc;
            margin: 10px 0;
        }
        &-btn{
            width: 60px;
            height: 30px;
            color: #666;
            background: #f3f4f5;
            font-size: 14px;
            float: right;
        }
        &-list{
            color: #999;
            width: 100%;
            padding: 5px 0;
            
            &-text{
                word-wrap:break-word;
            }
        }
        .border-bottom{
            border-bottom: 1px dashed #ccc;
        }

    }
.to-top{
    width: 40px;
    height: 50px;
    line-height: 50px;
    background: rgba(0,0,0,.5);
    color: #fff;
    text-align: center;
    position: fixed;
    bottom:10px;
    right: 10px;
}
</style>

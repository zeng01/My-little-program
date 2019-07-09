<template>
    <div>
        <!-- 轮播图 -->
        <swiper indicator-dots autoplay interval="5000" duration="1000" circular indicator-active-color="#fff">
        <block v-for="(item, index) in swiperList" :key="index.id">
            <swiper-item>
            <image :src="item.imgUrl" class="slide-image" width="100%"/>
            </swiper-item>
        </block>
        </swiper>
        <!-- 分类 -->
        <view class="nav">
            <a href="#">
                <i class="iconfont icon-notes">&#xe600;</i>
                <span>游记</span>
            </a>
            <a href="#">
                <i class="iconfont icon-book"></i>
                <span>攻略</span>
            </a>
            <a href="#">
                <i class="iconfont icon-search"></i>
                <span>搜索</span>
            </a>
            <a href="#">
                <i class="iconfont icon-email">&#xe636;</i>
                <span>联系我们</span>
            </a>
        </view>
        <!-- 内容 -->
        <view class="content">
            <view class="content-header">旅途风景/攻略</view>
            <navigator url="/pages/detail/main" open-type="navigate" hover-class="none" class="content-list" v-for="item in contentList" :key="item.id">
                <view class="content-list-left">
                    <img :src="item.imgUrl" alt="">
                </view>
                <view class="content-list-right">
                    <view class="title">{{item.title}}</view>
                    <view class="txt">{{item.text}}</view>
                    <view class="picview-other">   
                        <!-- <span class="po-date">日期：{{item.date}}</span> -->
                        <span class="po-name">作者：{{item.author}}</span>
                        <span class="po-view">浏览量：{{item.view}}</span>
                    </view>
                </view>
            </navigator>
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
            swiperList: [
                {id:1001,imgUrl:'../../static/images/banner01.jpg'},
                {id:1002,imgUrl:'../../static/images/banner02.jpg'},
                {id:1003,imgUrl:'../../static/images/banner03.jpg'},
                {id:1004,imgUrl:'https://images.unsplash.com/photo-1551446591-142875a901a1?w=640'}
            ],
            contentList:[
                {
                    id:1001,
                    imgUrl:'../../static/images/banner01.jpg',
                    view:23,
                    author:"admin",
                    date:2019-4-16,
                    title:'元阳，哈尼梯田的故乡',
                    text:"我们的行程从 伊兹密尔 出发到 塞尔丘克 、 博德鲁姆 、 代尼兹利 、 费特希耶 、 安塔利亚 、 卡帕多奇亚 ，最后从 内夫谢希尔 还车，全程主要是内陆高速、海滨公路、山区公路、内陆公路，路况非常好，基本都是双向两车道，全程柏油路。海滨和山区弯路多，相对曲折，天黑以后没有路灯，路况不熟悉尽量不要走夜路。我们走了两个小时D400夜路，瞪得10只眼珠+镜片都快掉下来了     A、高速国道公路路况：车速飞快，开到150后面的车还是会呼啸超过，完全忽视限速和监控。国道和公路是开放式的，高速行驶时，突然横穿马路的当地大叔大婶会把全车人吓傻，所以进村还是50以下吧。从 伊兹密尔 到 阿拉恰特 、 博德鲁姆 走了高速路，车很少路况不错，高速费很便宜，四次收费TRY14。土国的高速公路没有人工收费，高速路口有HGS和OGS 通道 标示，在AVIS租车时被告知走高速要使用HGS 通道 ，车辆通过时会显示扣费金额，还车时租车公司会从押金里一并扣减，完全不用操心。"
                },
                {
                    id:1002,
                    imgUrl:'../../static/images/banner02.jpg',
                    view:23,
                    author:"admin",
                    date:2019-4-16,
                    title:'元阳，哈尼梯田的故乡',
                    text:"我们的行程从 伊兹密尔 出发到 塞尔丘克 、 博德鲁姆 、 代尼兹利 、 费特希耶 、 安塔利亚 、 卡帕多奇亚 ，最后从 内夫谢希尔 还车，全程主要是内陆高速、海滨公路、山区公路、内陆公路，路况非常好，基本都是双向两车道，全程柏油路。海滨和山区弯路多，相对曲折，天黑以后没有路灯，路况不熟悉尽量不要走夜路。我们走了两个小时D400夜路，瞪得10只眼珠+镜片都快掉下来了     A、高速国道公路路况：车速飞快，开到150后面的车还是会呼啸超过，完全忽视限速和监控。国道和公路是开放式的，高速行驶时，突然横穿马路的当地大叔大婶会把全车人吓傻，所以进村还是50以下吧。从 伊兹密尔 到 阿拉恰特 、 博德鲁姆 走了高速路，车很少路况不错，高速费很便宜，四次收费TRY14。土国的高速公路没有人工收费，高速路口有HGS和OGS 通道 标示，在AVIS租车时被告知走高速要使用HGS 通道 ，车辆通过时会显示扣费金额，还车时租车公司会从押金里一并扣减，完全不用操心。"
                },
                {
                    id:1003,
                    imgUrl:'../../static/images/banner03.jpg',
                    view:23,
                    author:"admin",
                    date:2019-4-16,
                    title:'元阳，哈尼梯田的故乡',
                    text:"我们的行程从 伊兹密尔 出发到 塞尔丘克 、 博德鲁姆 、 代尼兹利 、 费特希耶 、 安塔利亚 、 卡帕多奇亚 ，最后从 内夫谢希尔 还车，全程主要是内陆高速、海滨公路、山区公路、内陆公路，路况非常好，基本都是双向两车道，全程柏油路。海滨和山区弯路多，相对曲折，天黑以后没有路灯，路况不熟悉尽量不要走夜路。我们走了两个小时D400夜路，瞪得10只眼珠+镜片都快掉下来了     A、高速国道公路路况：车速飞快，开到150后面的车还是会呼啸超过，完全忽视限速和监控。国道和公路是开放式的，高速行驶时，突然横穿马路的当地大叔大婶会把全车人吓傻，所以进村还是50以下吧。从 伊兹密尔 到 阿拉恰特 、 博德鲁姆 走了高速路，车很少路况不错，高速费很便宜，四次收费TRY14。土国的高速公路没有人工收费，高速路口有HGS和OGS 通道 标示，在AVIS租车时被告知走高速要使用HGS 通道 ，车辆通过时会显示扣费金额，还车时租车公司会从押金里一并扣减，完全不用操心。"
                },
                {
                    id:1004,
                    imgUrl:'../../static/images/banner04.jpg',
                    view:23,
                    author:"admin",
                    date:2019-4-16,
                    title:'元阳，哈尼梯田的故乡',
                    text:"我们的行程从 伊兹密尔 出发到 塞尔丘克 、 博德鲁姆 、 代尼兹利 、 费特希耶 、 安塔利亚 、 卡帕多奇亚 ，最后从 内夫谢希尔 还车，全程主要是内陆高速、海滨公路、山区公路、内陆公路，路况非常好，基本都是双向两车道，全程柏油路。海滨和山区弯路多，相对曲折，天黑以后没有路灯，路况不熟悉尽量不要走夜路。我们走了两个小时D400夜路，瞪得10只眼珠+镜片都快掉下来了     A、高速国道公路路况：车速飞快，开到150后面的车还是会呼啸超过，完全忽视限速和监控。国道和公路是开放式的，高速行驶时，突然横穿马路的当地大叔大婶会把全车人吓傻，所以进村还是50以下吧。从 伊兹密尔 到 阿拉恰特 、 博德鲁姆 走了高速路，车很少路况不错，高速费很便宜，四次收费TRY14。土国的高速公路没有人工收费，高速路口有HGS和OGS 通道 标示，在AVIS租车时被告知走高速要使用HGS 通道 ，车辆通过时会显示扣费金额，还车时租车公司会从押金里一并扣减，完全不用操心。"
                },
            ]
        }
    },
    created() {
        
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
        }
    },
}
</script>

<style lang="scss">
swiper{
    width:100%;
    image{
        width:100%;
    }
}
.nav{
    display: flex;
    a{
        flex:1;
        height:60px;
        margin:15px;
        text-align:center;
        font-size: 16px;
        color:#333;
        i{
            font-size:30px;
            border-radius:50%;
            background:#f54;
            color:#fff;
            
            line-height:60px;
        }
    }
}

.content{
    margin: 20px 10px;
    .content-header{
        height: 30px;
        font-size: 16px;
        background: #77c9d4;
        line-height: 30px;
        padding: 0 10px;
        color:#fff;

    }
    .content-list{
        padding: 10px 10px 0 10px;
        height: 80px;
        .content-list-left{
            width: 34%;
            height: 80px;
            float: left;
            margin-bottom: 20px;
            img{
                width:100%;
                height: 100%;
            }
        }
        .content-list-right{
            width: 60%;
            height: 80px;
            padding-left: 20px;
            float: right;
            overflow: hidden;
            margin-bottom: 20px;
            .title{
                color:#77c9d4;
                font-size: 16px;
                font-weight: 700;
            }
            .txt{
                height: 35px;
                display: -webkit-box;
                -webkit-box-orient: vertical;
                -webkit-line-clamp: 2;
                overflow: hidden;
                margin: 2px 0;
                color: #333;
                
            }
            .picview-other{
                height: 20px;
                font-size: 12px;
                color: #666;
                .po-name{
                    margin-right: 10px;
                }
            }
        }
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

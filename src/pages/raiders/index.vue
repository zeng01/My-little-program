<template>
    <div>
        <scroll-view scroll-y :scroll-with-animation="true" @tap="selectCategory" :style="{height:(windowHeight-10)+'px'}" class="menu">
            <block v-for="item in menuList" :key="item.id">
                <view :data-id="item.id" :data-index="index" :class="['menu_list',index === selectedIndex ?'active':'']">{{item.title}}</view>
            </block>
        </scroll-view>
        <scroll-view scroll-y :scroll-with-animation="true" :style="{height:(windowHeight-10)+'px'}" class="raiders">
            <navigator
          url="/pages/detail/main"
          open-type="navigate"
          hover-class="none" class="raiders-list" v-for="(item, index) in raidersList" :key="item.menu_id">
            <text v-if="item.length>0" class="notes">暂无数据</text>
           <text :data-menu-id="item.menu_id" class="title" v-else>{{index+1}}、{{item.name}}</text>
        </navigator> 
        </scroll-view>
           
    </div>
</template>

<script>
export default {
    data() {
        return {
            raidersList:[],
            menuList:[
                {id:101,title:"风景",
                    children:[
                        {menu_id:1,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:2,name:"凝滞的生活，一旦被打开，便幸福四溢"},
                        {menu_id:3,name:"碎片化时代，我们应该怎样去写作"},
                        {menu_id:4,name:"张家界游玩最佳季节，景点建议游玩时间+每日开放时间"},
                        {menu_id:5,name:"盘点江西十大美食街：江西吃货最喜欢去逛的美食街"},
                        {menu_id:6,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:7,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:8,name:"凝滞的生活，一旦被打开，便幸福四溢。"},
                        {menu_id:9,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:10,name:"张家界游玩最佳季节，景点建议游玩时间+每日开放时间"},
                        {menu_id:1014,name:"你好，大梅沙"},
                        {menu_id:1015,name:"西冲烧烤日"},
                        {menu_id:1016,name:"烈日如歌|写给自己的一封夏日情诗，走进富春江畔"},
                        {menu_id:1017,name:"萨瓦迪，随时光倒流的琅勃拉邦"},
                        {menu_id:1018,name:"打卡龙岩新地标，一场说走就走的客家寻味之旅"},
                        {menu_id:1019,name:"深夜空降暹罗_漫天神佛的微笑国度"},
                        {menu_id:1020,name:"少林禅武镇中天，嵩高维岳鼎千年”——周末两天徒步嵩山"},
                        {menu_id:1021,name:"行走在山野间，永不停留（细数一年来的户外穿越露营经历）"},
                        {menu_id:1022,name:"『纪念』以山之名 | 朝圣贡嘎，追梦逐风"},
                        {menu_id:1023,name:"梧桐山的旅游心情梧桐山的旅游心情梧桐山的旅游心情梧桐山的旅游心情"},
                        {menu_id:1024,name:"玫瑰海岸的美好一天"},
                        {menu_id:1025,name:"你好，大梅沙"},
                        {menu_id:1026,name:"西冲烧烤日"},
                        {menu_id:1027,name:"烈日如歌|写给自己的一封夏日情诗，走进富春江畔"},
                        {menu_id:1028,name:"萨瓦迪，随时光倒流的琅勃拉邦"},
                        {menu_id:1029,name:"打卡龙岩新地标，一场说走就走的客家寻味之旅"},
                        {menu_id:1030,name:"深夜空降暹罗_漫天神佛的微笑国度"},
                        {menu_id:1031,name:"少林禅武镇中天，嵩高维岳鼎千年”——周末两天徒步嵩山"},
                        {menu_id:1032,name:"行走在山野间，永不停留（细数一年来的户外穿越露营经历）"},
                        {menu_id:1033,name:"『纪念』以山之名 | 朝圣贡嘎，追梦逐风"},
                    ]
                },
                {id:102,title:"美食",
                    children:[
                        {menu_id:11,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:12,name:"美食与美食攻略：拆解重组美食攻略的组合形式"},
                        {menu_id:13,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:14,name:"美食 ‖ 美食，不仅是美食本身！"},
                        {menu_id:15,name:"青岛美食去哪儿吃 八大条小吃美食街任你挑选"},
                        {menu_id:16,name:"17种小时候过年必吃的春节传统美食！"},
                        {menu_id:17,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:18,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:19,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:20,name:"17种小时候过年必吃的春节传统美食"},
                        
                    ]
                },
                {id:103,title:"旅游心情",
                    children:[
                        {menu_id:31,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:32,name:"凝滞的生活，一旦被打开，便幸福四溢"},
                        {menu_id:33,name:"碎片化时代，我们应该怎样去写作"},
                        {menu_id:34,name:"张家界游玩最佳季节，景点建议游玩时间+每日开放时间"},
                        {menu_id:35,name:"盘点江西十大美食街：江西吃货最喜欢去逛的美食街"},
                        {menu_id:36,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:37,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:38,name:"凝滞的生活，一旦被打开，便幸福四溢。"},
                        {menu_id:39,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:40,name:"张家界游玩最佳季节，景点建议游玩时间+每日开放时间"}
                    ]
                },
                {id:104,title:"旅游轶事",
                    children:[
                        {menu_id:41,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:42,name:"美食与美食攻略：拆解重组美食攻略的组合形式"},
                        {menu_id:43,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:44,name:"美食 ‖ 美食，不仅是美食本身！"},
                        {menu_id:45,name:"青岛美食去哪儿吃 八大条小吃美食街任你挑选"},
                        {menu_id:46,name:"17种小时候过年必吃的春节传统美食！"},
                        {menu_id:47,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:48,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:49,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:50,name:"17种小时候过年必吃的春节传统美食"},
                        
                    ]
                },
                {id:105,title:"旅行家专栏",
                     children:[
                        {menu_id:51,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:52,name:"凝滞的生活，一旦被打开，便幸福四溢"},
                        {menu_id:53,name:"碎片化时代，我们应该怎样去写作"},
                        {menu_id:54,name:"张家界游玩最佳季节，景点建议游玩时间+每日开放时间"},
                        {menu_id:55,name:"盘点江西十大美食街：江西吃货最喜欢去逛的美食街"},
                        {menu_id:56,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:57,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:58,name:"凝滞的生活，一旦被打开，便幸福四溢。"},
                        {menu_id:59,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                        {menu_id:60,name:"张家界游玩最佳季节，景点建议游玩时间+每日开放时间"}
                    ]
                },
                {id:106,title:"攻略推荐",
                    children:[
                        {menu_id:61,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:62,name:"美食与美食攻略：拆解重组美食攻略的组合形式"},
                        {menu_id:63,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:64,name:"美食 ‖ 美食，不仅是美食本身！"},
                        {menu_id:65,name:"青岛美食去哪儿吃 八大条小吃美食街任你挑选"},
                        {menu_id:66,name:"17种小时候过年必吃的春节传统美食！"},
                        {menu_id:67,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:68,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:69,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:70,name:"17种小时候过年必吃的春节传统美食"},
                        
                    ]
                },
                {id:107,title:"最新活动",
                     children:[
                        {menu_id:72,name:"凝滞的生活，一旦被打开，便幸福四溢"},
                        {menu_id:73,name:"碎片化时代，我们应该怎样去写作"},
                        {menu_id:74,name:"张家界游玩最佳季节，景点建议游玩时间+每日开放时间"},
                        {menu_id:75,name:"盘点江西十大美食街：江西吃货最喜欢去逛的美食街"},
                        {menu_id:76,name:"春日的诗，丰子恺的画，醉了整个春天。"},
                    ]
                },
                {id:108,title:"从南到北",
                    children:[
                        {menu_id:81,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:82,name:"美食与美食攻略：拆解重组美食攻略的组合形式"},
                        {menu_id:83,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:84,name:"美食 ‖ 美食，不仅是美食本身！"},
                        {menu_id:85,name:"青岛美食去哪儿吃 八大条小吃美食街任你挑选"},
                        {menu_id:86,name:"17种小时候过年必吃的春节传统美食！"},
                        {menu_id:87,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:88,name:"【香港美食】10家必吃香港美食推荐(含米其林)-尖沙咀"},
                        {menu_id:89,name:"关于美食论，什么是美食？你理解的美食是什么"},
                        {menu_id:90,name:"17种小时候过年必吃的春节传统美食"},
                        
                    ]
                },
                {id:109,title:"登山徒步",
                    children:[
                        {menu_id:1001,name:"梧桐山的旅游心情梧,夏日情诗,徒步嵩山"},
                        {menu_id:1002,name:"玫瑰海岸的美好一天"},
                        {menu_id:1003,name:"你好，大梅沙"},
                        {menu_id:1004,name:"西冲烧烤日"},
                    ]
                },
                {id:110,title:"轶事",
                    children:[
                        {menu_id:1005,name:"烈日如歌|写给自己的一封夏日情诗，走进富春江畔"},
                        {menu_id:1006,name:"萨瓦迪，随时光倒流的琅勃拉邦"},
                        {menu_id:1007,name:"打卡龙岩新地标，一场说走就走的客家寻味之旅"},
                        {menu_id:1008,name:"深夜空降暹罗_漫天神佛的微笑国度"},
                        {menu_id:1009,name:"少林禅武镇中天，嵩高维岳鼎千年”——周末两天徒步嵩山"},
                        {menu_id:1010,name:"行走在山野间，永不停留（细数一年来的户外穿越露营经历）"},
                        {menu_id:1011,name:"『纪念』以山之名 | 朝圣贡嘎，追梦逐风"},
                        {menu_id:1012,name:"梧桐山的旅游心情梧桐山的旅游心情梧桐山的旅游心情梧桐山的旅游心情"},
                        {menu_id:1013,name:"玫瑰海岸的美好一天"},
                    ]
                },
                {id:111,title:"旅游心情",
                    children:[
                        
                    ]
                },
                {id:112,title:"旅游轶事",
                    children:[]
                },
                {id:113,title:"旅行家专栏",
                    children:[]
                },
                {id:114,title:"攻略推荐",
                    children:[]
                },
                {id:115,title:"最新活动",
                    children:[]
                },
                {id:116,title:"从南到北",
                    children:[]
                },
                {id:117,title:"风景",
                    children:[]
                },
                {id:118,title:"轶事",
                    children:[]
                },
                {id:119,title:"旅游心情",
                    children:[]
                },
                {id:120,title:"旅游轶事",
                    children:[]
                },
                {id:121,title:"旅行家专栏",
                    children:[]
                },
                {id:122,title:"攻略推荐",
                    children:[]
                },
                {id:123,title:"最新活动",
                    children:[]
                },
                {id:124,title:"从南到北",
                    children:[]
                }
            ],
            windowHeight: 0, // 屏幕高度
            selectedIndex: 0, // 选中的索引，默认是0
        }
    },
    async onLoad (options) {
        // 获取系统信息
        const systemInfo = wx.getSystemInfoSync()
        this.windowHeight = systemInfo.windowHeight
        // 默认选中第一个
        this.raidersList = this.menuList[0].children
    },
    methods: {
        selectCategory (e) {
        if (e.target.dataset.index === this.selectedIndex) return

        this.selectedIndex = e.target.dataset.index

        this.raidersList = this.menuList[this.selectedIndex].children
        }
    }
}
</script>

<style lang="scss">
    .raiders-list{
        height: 30px;
        line-height: 30px;
        font-size: 16px;
        padding: 5px 10px;
        border-bottom: 1px double #f1f2f3;
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 1;
        overflow: hidden;
    }
    .menu{
        float: left;
        width: 26%;
        height: 100%;
        background-color: #f4f4f4;
        overflow: hidden;
        .menu_list{
            padding: 10px 0;
            text-align: center;
            font-size: 14px;
        }
        /*隐藏滚动条*/
        ::-webkit-scrollbar {
            width: 0;
            height: 0;
            color: transparent;
        }
    }

    .active{
        background: #fff;
        border-right: 3px solid #57bc90;
    }

    .raiders{
        float: right;
        width: 72%;
        /*隐藏滚动条*/
        ::-webkit-scrollbar {
            width: 0;
            height: 0;
            color: transparent;
        }
        .notes{
            padding: 30px 0;
            text-align: center;
        }
    }

    
</style>

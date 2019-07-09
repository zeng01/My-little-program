<template>
    <div>
        <navigator
          url="#"
          open-type="navigate"
          hover-class="none" class="raiders-list" v-for="(item, index) in raidersList" :key="item.id">
           <text class="title">{{index+1}}、{{item.title}}</text>
        </navigator> 
           
    </div>
</template>

<script>
export default {
    data() {
        return {
            raidersList:[
                {id:1001,title:"梧桐山的旅游心情梧桐山的旅游心情梧桐山的旅游心情梧桐山的旅游心情"},
                {id:1002,title:"玫瑰海岸的美好一天"},
                {id:1003,title:"你好，大梅沙"},
                {id:1004,title:"西冲烧烤日"},
                {id:1005,title:"玫瑰海岸的美好一天"}
            ]
        }
    },
}
</script>

<style lang="scss">
    .raiders-list{
        height: 30px;
        line-height: 30px;
        font-size: 16px;
        padding: 0 10px;
        border-bottom: 1px solid #ccc;
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 1;
        overflow: hidden;
    }
</style>

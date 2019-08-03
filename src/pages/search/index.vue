<template>
    <view>
        <view class="search">
            <input type="search" name="search" class="searchIndex" v-model="searchText" auto-focus>
        </view>
        <view>{{searchText}}</view>
    </view>
</template>

<script>
export default {
    data() {
        return {
            searchText:''
        }
    },
}
</script>

<style lang="scss">
    .search{
        .searchIndex{
            height: 36px;
            border: 1px solid #ccc;
        }
    }
</style>

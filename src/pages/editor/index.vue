<template>
    <view>
        <editor
        id="editor"
        class="ql-container"
        placeholder="请输入"
        showImgSize
        showImgToolbar
        showImgResize
        @ready="onEditorReady" @input="onContentChange">
        </editor>
        <view><button @tap="clickShowText">显示结果</button></view>
        <view>
            <rich-text :nodes="nodes"></rich-text>
        </view>
        <view>
            <button @tap="upload">上传图片</button>
        </view>
    </view>
</template>

<script>
export default {
    data() {
        return {
            content:'',
            content_html:'',
            nodes: [{
                name: 'div',
                attrs: {
                    class: 'div_class',
                    style: 'line-height: 60px; color: red;'
                },
                children: [{
                    type: 'text',
                    text: ''
                }]
            }]
        }
    },
    methods: {
        onEditorReady() {
            const that = this
            wx.createSelectorQuery().select('#editor').context(function (res) {
                that.editorCtx = res.context
                console.log("初始化成功：" + wx.getStorageSync("content"))
                if (wx.getStorageSync("content")) { // 设置~历史值
                    that.editorCtx.insertText(wx.getStorageSync("content")) // 注意：插入的是对象
                }
            }).exec()
        },
        onContentChange(e) {
            this.content=e.target.html
            wx.setStorageSync('content','e.target.html')
        },
        clickShowText(e) {
            this.nodes=this.content
            
        },
    },
    
}
</script>

<style>

</style>

<template>
  <view style="background-color: #c8c7cc;">
    <editor id="editor" class="ql-container" :placeholder="placeholder" @ready="onEditorReady"></editor>

  </view>
</template>

<script>
export default {
  name: "mine-personal",
  data() {
    return {
      placeholder: '开始输入...'
    }
  },
  methods: {
    onEditorReady() {
      // #ifdef MP-BAIDU
      this.editorCtx = requireDynamicLib('editorLib').createEditorContext('editor');
      // #endif

      // #ifdef APP-PLUS || H5 ||MP-WEIXIN
      uni.createSelectorQuery().select('#editor').context((res) => {
        this.editorCtx = res.context
      }).exec()
      // #endif
    },
    undo() {
      this.editorCtx.undo()
    }
  }
}
</script>

<style scoped>

</style>
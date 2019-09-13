<template>
  <div class="editor">
    <h1>エディター画面</h1>
    <div class="editorWrapper">
      <textarea class="markdown" v-model="markdown"></textarea>
      <div class="preview" v-html="preview()"></div>
    </div>
  </div>
</template>

<script>
import marked from "marked";
export default {
    name: "editor",
    //prop["user"]
    data() {
        return {
            markdown: "",
        };
    },
    methods: {
        preview: function () {
            return marked(this.markdown);
        }
    }
};
</script>
<style lang="scss" scoped>
.editorWrapper {
    display: flex;
    width:100%;
}
.markdown {
    width: 50%;
    height: 500px;
}
.preview,
.preview * {
    width: 50%;
    text-align: left;
}
</style>
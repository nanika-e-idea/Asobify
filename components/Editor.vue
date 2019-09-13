<template>
  <div class="editor">
    <h1>エディター画面</h1>
    <sapn>{{ user.displayName }}</sapn>
    <div class="editorWrapper">
      <div class="memoListWrapper">
        <div class="memoList" v-for="(memo, index) in  memos" :key="index" @click="selectMemo(index)" :data-selected="index == selectedIndex">
          <p class="memoTitle">{{ displayTitle(memo.markdown) }}</p>
        </div>
        <button class="addMemoBtn" @click="addMemo">メモの追加</button>
      </div>
      <textarea class="markdown" v-model="markdown"></textarea>
      <div class="preview" v-html="preview()"></div>
    </div>
  </div>
</template>

<script>
import marked from "marked";
export default {
    name: "editor",
    prop: ["user"],
    data() {
        return {
            memos: [
                {
                    markdown: "",
                }
            ],
            selectedIndex: 0,
        };
    },
    methods: {
        addMemo: function() {
            this.memos.push({
                markdown: "新しいメモ"
            });
        },
        selectMemo: function(index) {
            this.selectedIndex = index;
        },
        preview: function() {
            return marked( this.memos[this.selectedIndex].markdown );
        },
        displayTitle: function(text) {
            return text.split(/\n/)[0];
        },
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
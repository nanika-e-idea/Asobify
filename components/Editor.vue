<template>
  <div class="editor">
    <h1>エディター画面</h1>
    <!--<sapn>{{ user.displayName }}</sapn>-->
    <div class="editorWrapper">
      <div class="memoListWrapper">
        <div class="memoList" v-for="(memo, index) in  memos" :key="index" @click="selectMemo(index)" :data-selected="index == selectedIndex">
          <p class="memoTitle">{{ displayTitle(memo.markdown) }}</p>
        </div>
        <button class="addMemoBtn" @click="addMemo">メモの追加</button>
        <button class="deleteMemoBtn" v-if="memos.length > 1" @click="deleteMemo">選択中のメモを削除</button>
      </div>
      <textarea class="markdown" v-model="memos[selectedIndex].markdown"></textarea>
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
        deleteMemo: function() {
            this.memos.splice(this.selectedIndex, 1);
            if (this.selectedIndex > 0) {
                this.selectedIndex--;
            }
        },
    },
};
</script>
<style lang="scss" scoped>
.editorWrapper {
    display: flex;
}
.memoListWrapper {
    width:20%;
    border-top: solid 1px #000;
}
.memoList {
    padding: 10px;
    box-sizing: border-box;
    text-align: left;
    border-bottom: solid 1px #000;
    &:nth-child(even){
        background-color: #ccc;
    }
    &[data-selected="true"]{
        background-color: #cdd;
    }
}
.memoTitle {}
.markdown {
    width: 40%;
    height: 500px;
}
.preview,
.preview * {
    width: 40%;
    text-align: left;
}

</style>
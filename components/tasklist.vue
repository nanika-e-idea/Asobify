<template>
<div class="tasklist">
  <listitem />
  <listitem />
  <listitem />
  <listitem />
  <listitem />
</div>
</template>

<script>
import listitem from '~/components/taskListItem.vue'
export default {
  components: {
      listitem,
  },
}
</script>

<style lang="scss" scoped>
@import '~/assets/scss/base.scss';

.tasklist{
    display: block;
    width: calc(100% - 20px);
    //max-width: 600px;
    background-color: #eee;
    .task{
        width: 100%;
        margin-bottom: 4px;
        &:nth-child(odd){
            background-color: white;
        }
        &:nth-child(even){
            background-color: #def;
        }
        &:first-child{
            border-top: solid 1px #222;
        }
        &:last-child{
            margin-bottom: 0;
            border-bottom: solid 1px #222;
        }
    }
}
.schedule{
    display: flex;
    justify-content: center;
}
</style>
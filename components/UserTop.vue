<template>
    <div>
        <h2>Task List</h2>
        <task />
        <editor />
    </div>
</template>

<script>
import firebase from "~/plugins/firebase.js"
import task from '~/components/tasklist.vue'
import editor from '~/components/Editor.vue'
export default {
    name: "usertop",
    components: {
        task,
        editor,
    },
}
</script>

<style lang="scss" scoped>
@import '~/assets/scss/base.scss';

</style>
<template>
    <div>
        <h2>Task List</h2>
        <task />
    </div>
</template>

<script>
import firebase from "~/plugins/firebase.js"
import task from '~/components/tasklist.vue'
export default {
    name: "usertop",
    components: {
        task,
    },
}
</script>

<style lang="scss" scoped>
@import '~/assets/scss/base.scss';



</style>
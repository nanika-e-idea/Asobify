<template>
    <div class="header">
        <div class="h-space"></div>
        <div class="h-box">
            <v-btn @click="logout">ログアウト</v-btn>
        </div>
    </div>
</template>

<script>
import firebase from '~/plugins/firebase'

export default {
  name:'headercomp',
  props: ["user"],
  data() {
      return{}
  },
  methods: {
    logout: function() {
      firebase.auth().signOut();
    }
  },
}
</script>

<style lang="scss" scoped>
$hheight: 50px; 
.header{
    display: block;
    position: relative;
    width: 100%;
    height: $hheight;
    .h-space{
        display: block;
        position: relative;
        width: 100%;
        height: $hheight;
    }
    .h-box{
        display: block;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: $hheight;
        background-color: #999;
    }
}
</style>
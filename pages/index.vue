<template>
  <div class="container">
    <Home v-if="!isLogin" />
    <UserTop v-if="isLogin" />
  </div>
</template>

<script>
import Home from '~/components/Home.vue'
import UserTop from '~/components/UserTop.vue'
import firebase from '~/plugins/firebase'

export default {
  name: "app",
  components: {
    Home,
    UserTop
  },
  data() {
    return {
      isLogin: false
    }
  },
  created: function() {
    firebase.auth().onAuthStateChanged(user => {
      console.log(user);
      if (user) {
        this.isLogin = true;
      } else {
        this.isLogin = false;
      };
    });
  },
}
</script>

<style lang="scss">
@import '~/assets/scss/base.scss';
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>

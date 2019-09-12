<template>
    <div id="home">
        <h1 v-html="msg" />
        <v-btn @click="firebaseLogin">Twitterでログイン</v-btn>
    </div>
</template>
<script>
import firebase from '~/plugins/firebase'

export default {
  name: "home",
  data() {
    return {
      msg: "welcome to Asobify"
    };
  },
  methods: {
    firebaseLogin: function() {
      firebase
      .auth()
      .signInWithRedirect(new firebase.auth.TwitterAuthProvider());
    }
  },
};
</script>
<template>
  <v-app>
    <v-app-bar app>
      <v-btn depressed to="/">Messages</v-btn>
      <v-btn depressed to="/new-message">New Message</v-btn>
      <v-spacer />
      <v-btn v-if="!$store.state.token" depressed to="/register"
        >Register</v-btn
      >
      <v-btn v-if="!$store.state.token" to="/login">Login</v-btn>
      <v-btn v-if="$store.state.token" @click="logoutHandler">Logout</v-btn>
    </v-app-bar>

    <v-content>
      <br />
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",
  methods: {
    logoutHandler() {
      this.$store.dispatch("logout");
    },
  },
};
</script>

<template>
  <div class="home">
    <Farewell msg="Hi, DockerLead!" />
    <div v-if="!$auth.loading">
      <!-- show login when not authenticated -->
      <b-button variant="success" v-if="!$auth.isAuthenticated" @click="login"
        >Log in</b-button
      >
      <!-- show logout when authenticated -->
      <b-button variant="danger" v-if="$auth.isAuthenticated" @click="logout"
        >Log out</b-button
      >
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Farewell from "@/components/Farewell.vue";

export default {
  name: "Home",
  components: {
    Farewell
  },
  methods: {
    // Log the user in
    login() {
      this.$auth.loginWithRedirect();
    },
    // Log the user out
    logout() {
      this.$auth.logout({
        returnTo: window.location.origin
      });
    }
  }
};
</script>

<style lang="scss" scoped>
button {
  margin: 2rem;
}
</style>

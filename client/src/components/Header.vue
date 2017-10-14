<template>
  <v-toolbar dark fixed class="xs">
      <v-toolbar-title class="mr-4">
        <router-link to="/#/" tag="span" style="cursor: pointer">
        App name
        </router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn>
          Browse
        </v-btn>
        <v-btn router :to="'/register'" v-if="!$store.state.isUserLoggedIn">
          Sign Up
        </v-btn>
        <v-btn router :to="'/login'" v-if="!$store.state.isUserLoggedIn">
          Login
        </v-btn>
        <v-btn @click="logout" v-if="$store.state.isUserLoggedIn">
          Log out
        </v-btn>
      </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  methods: {
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push('/')
    }
  }
}
</script>

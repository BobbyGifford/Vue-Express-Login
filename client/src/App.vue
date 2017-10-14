<template>
  <v-app dark>
    <app-header class="pb-2"></app-header>
      <main>
        <v-container fluid>
          <router-view></router-view>
        </v-container>
      </main>
  </v-app>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>

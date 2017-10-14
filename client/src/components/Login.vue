<template>
  <v-form @submit.prevent="login" autocomplete="off">
    <v-layout column>
      <v-flex >
        <div class="elevation-2 pa-2">
            <h1 class="white--text">Login</h1>

            <v-text-field
            type="email"
            name="email"
            placeholder="email"
            v-model="email"></v-text-field>

            <br >

            <v-text-field 
            type="password"
            name="password"
            placeholder="password"
            v-model="password"></v-text-field>

            <br>
            <!-- Make error message go away on successful login/register -->
            <div class ="error white--text" v-html="error"></div>

            <v-btn @click="login">Login</v-btn>
          </div>

        </div>
      </v-flex>
    </v-layout>
  </v-form>
</template>

<script>
import AuthenicationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login () {
      try {
        const response = await AuthenicationService.login({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
        this.$router.push('/')
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

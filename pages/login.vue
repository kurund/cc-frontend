<template>
  <div class="login">
    <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-12">
      <form @submit.prevent="userLogin">
        <h2 class="text-2xl font-bold">Enter your credentials</h2>
        <div class="mt-8">
          <div class="flex flex-col gap-8">
            <label class="block">
              <span class="text-gray-700">Email address</span>
              <input
                v-model="login.identifier"
                type="email"
                class="input-field"
                placeholder="volunteer@example.com"
              />
            </label>

            <label class="block">
              <span class="text-gray-700">Password</span>
              <input
                v-model="login.password"
                type="password"
                class="input-field"
                placeholder=""
              />
            </label>
          </div>
        </div>

        <div class="p-3">
          <button class="blue-button">Login</button>
        </div>
      </form>
      <Notification v-if="error" type="danger" :message="error" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      login: {
        identifier: '',
        password: '',
      },
      error: null,
    }
  },
  methods: {
    async userLogin() {
      this.error = null
      try {
        await this.$auth.loginWith('local', {
          data: this.login,
        })

        this.$router.push('/')
      } catch (e) {
        this.error = 'Email or password invalid.'
      }
    },
  },
})
</script>

<style scoped>
.login {
  @apply relative flex flex-col justify-center min-h-screen bg-gray-50 sm:items-center sm:pt-0;
}
</style>

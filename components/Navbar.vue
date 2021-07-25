<template>
  <div
    v-if="$auth.loggedIn"
    class="container mx-auto flex p-3 space-x-2 justify-end"
  >
    <div class="flex space-x-2">
      <div class="py-2 px-4">
        {{ $auth.user.email }}
      </div>
      <div>
        <button class="blue-button" @click="logout">Logout</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    async logout() {
      await this.$auth.logout()
      this.$router.push('/login')
    },
  },
}
</script>

<style>
</style>
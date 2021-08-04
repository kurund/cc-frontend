<template>
  <div v-if="$auth.loggedIn" class="container mx-auto flex p-3">
    <div class="flex-grow py-2 px-4">
      <div class="flex space-x-2">
        <div class="underline"><NuxtLink to="/">Dashboard</NuxtLink></div>
        <div class="underline">
          <NuxtLink to="/call">IVR Call</NuxtLink>
        </div>
        <div class="underline">
          <NuxtLink to="/contacts">Contacts</NuxtLink>
        </div>
      </div>
    </div>
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

<style></style>

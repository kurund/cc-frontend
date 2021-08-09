<template>
  <div :class="`${type}`" role="alert">
    {{ message }}
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'Notification',
  props: {
    type: {
      type: String,
      default: 'success',
      validator: (val) => ['danger', 'success'].includes(val),
    },
    message: {
      type: String,
      default: '',
    },
  },
})
</script>

<style scoped>
.danger {
  @apply bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative;
}
</style>

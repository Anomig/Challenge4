<script setup>
  const props = defineProps({
    messages: Array
  })
</script>

<template>
  <h2>Comments</h2>
  <ul>
    <li v-for="(message, index) in messages" :key="index">
      <strong>{{ message.user }}</strong>: {{ message.text }}
    </li>
  </ul>
</template>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0.5rem 0;
}
</style>

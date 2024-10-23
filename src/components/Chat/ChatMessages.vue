<script setup>
  import {onMounted, reactive} from 'vue';

  const messages = reactive([]);

  onMounted(() => {
    fetch('https://les003-mongodn.onrender.com/api/v1/messages')
      .then(response => response.json())
      .then(data => {
        messages.push (...data.data.messages);
      });
  });

  function handleNewMessage(message){
    messages.push(message);
  }
</script>

<template>
  <h2>Comments</h2>
  <u>
    <li v-for="message in messages">
      <strong>{{ message.user }}</strong>: {{ message.text }}
    </li>
  </u>
</template>

<style scoped>

</style>

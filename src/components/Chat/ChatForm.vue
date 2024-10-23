<script setup>
  import { ref, reactive } from 'vue';

  const newMessage = ref('');

  function sendMessage(emit){
    if(newMessage.value.trim() === ''){
      return;
    }
  }

  const messageData = {
    user: 'Anonymous',
    tekst: newMessage.value
  }

  fetch('https://les003-mongodn.onrender.com/api/v1/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(messageData)
  })
  .then(response => response.json())
  .then(data=>{
    emit('newMessage', data.data.message);
    newMessage.value = '';
   })
  .catch(error => {
    console.error('Error:', error);
  })
</script>

<template>
  <div class="form">
    <input  type="text" placeholder="Type your message here" />
    <button @click="doit">Send</button>
  </div>
</template>

<style scoped>

</style>

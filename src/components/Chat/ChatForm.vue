<script setup>
  import {ref} from 'vue';

  const newMessage = ref('');
  const emit = defineEmits(['new-message']);

  function sendMessage() {
    if (newMessage.value.trim() === '') return; 

    const messageData = {
      user: 'Anonymous', 
      text: newMessage.value
    };
    fetch('https://lab5-p379.onrender.com/api/v1/messages/', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(messageData)
    })
    .then(response =>{
      if(response.ok){
        return response.json();
      } else {
        throw new Error('Failed to post message');
      }
    })
    .then(data => {
      emit('new-message', data.data.messageData);
      text.value = '';
    })
    .catch(error => {
      console.error('Error posting message:', error);
    });

  }
</script>

<template>
  <div class="form">
    <input v-model="newMessage" type="text" placeholder="Type your message here" />
    <button @click="sendMessage">Send</button>
  </div>
</template>

<style scoped>
.form {
  display: flex;
  gap: 0.5rem;
}
input {
  flex-grow: 1;
  padding: 0.5rem;
}
button {
  padding: 0.5rem 1rem;
}
</style>

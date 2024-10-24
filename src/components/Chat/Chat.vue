<script setup>
  import{reactive, onMounted} from 'vue';
  import ChatMessages from './ChatMessages.vue';
  import ChatForm from './ChatForm.vue';

  const messages = reactive([]);

 onMounted(async () => {
    const response = await fetch('https://lab5-p379.onrender.com/api/v1/messages/');
    const data = await response.json();
    messages.push(...data);
  });

  const addMessage = (newMessage) => {
    messages.unshift(newMessage);
  }
</script>

<template>
  <ChatMessages :messages="messages" />
  <ChatForm @new-message="addMessage" />
</template>

<style scoped>

</style>

<script setup>
import ChatMessages from './ChatMessages.vue';
import ChatForm from './ChatForm.vue';

function onNewMessage(message){
    ChatMessages.handleNewMessage(message);
}
</script>

<template>
    <ChatMessages @new-message="onNewMessage" />
    <ChatForm @new-message="onNewMessage"/>
</template>

<style scoped>

</style>

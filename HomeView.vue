<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import axios from "axios";

export default {
  name: "HomeView",
  data(){
    return {
      message: "",
    };
  },
}


async function sendMessage() {
  await axios.post('http://localhost:3200/test', {
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({ message: this.message }),
  });
  const results = await response.json();
}
</script>

<template>
  <div>
    <input type="text" v-model="message" placeholder="Type your message" />
    <button @click="sendMessage">Send</button>
  </div>
</template>

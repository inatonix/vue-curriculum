<script setup lang="ts">
import { ref } from "vue";
const tweet = ref("");

const onSubmit = () => {
  console.log(tweet.value);
  tweet.value = "";
};
</script>

<template>
  <div>
    <form @click.prevent class="tweet-form">
      <input type="text" placeholder="What's happening?" v-model="tweet" />
      <button @click="onSubmit">Tweet</button>
    </form>
  </div>
</template>

<style scoped>
.tweet-form {
  height: 6em;
  display: flex;
  flex-direction: column;
  will-change: filter;
  transition: filter 300ms;
}

.tweet-form input {
  height: 2em;
  padding: 1.5em;
  border: 1px solid #646cffaa;
  border-radius: 0.5em;
  margin-bottom: 1em;
}

.tweet-form button {
  border-radius: 0.5em;
  background-color: #646cff;
  color: white;
}
</style>

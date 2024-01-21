<script setup lang="ts">
import { ref } from "vue";
import { Tweet } from "../types/Tweet";

const tweets = ref<Tweet[]>([{ id: "1", text: "Hello, world!" }]);
</script>

<template>
  <div>
    <ul>
      <li v-for="tweet in tweets" :key="tweet.id">
        {{ tweet.text }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  font-size: 1.5em;
  border: 1px solid #dadcffaa;
}

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

<script setup lang="ts">
import { ref } from "vue";
import { Tweet } from "../types/Tweet";

const tweets = ref<Tweet[]>([
  { id: "1", text: "Hello, Vue 3!" },
  { id: "2", text: "Hello, Vite!" },
]);
</script>

<template>
  <div class="tweet-list">
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
  margin: 0;
}

.tweet-list li {
  padding: 1em;
  border-bottom: 1px solid #ccc;
  font-size: 1.5em;
}
</style>

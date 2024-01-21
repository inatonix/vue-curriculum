<script setup lang="ts">
import TweetForm from "./components/TweetForm.vue";
import TweetList from "./components/TweetList.vue";
import { ref } from "vue";
import { Tweet } from "./types/Tweet";

const tweets = ref<Tweet[]>([
  { id: "1", text: "Hello, Vue 3!" },
  { id: "2", text: "Hello, Vite!" },
]);

const onSubmitForm = (tweet: string) => {
  tweets.value.push({ id: String(Math.random()), text: tweet });
};
</script>

<template>
  <div><TweetForm @submit="onSubmitForm" /> <TweetList :tweets="tweets" /></div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

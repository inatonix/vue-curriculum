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
  <div class="container">
    <div class="header">
      <button>Settings</button>
    </div>
    <TweetForm @submit="onSubmitForm" />
    <TweetList :tweets="tweets" />
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.header {
  display: flex;
  justify-content: flex-end;
  height: 100px;
}

.header button {
  border: none;
  margin: 20px;
  border-radius: 0.5em;
  background-color: #6cd4f1;
  color: white;
  width: 200px;
  font-size: 1.5em;
}
</style>

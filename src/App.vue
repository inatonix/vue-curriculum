<script setup lang="ts">
import TweetForm from "./components/TweetForm.vue";
import TweetList from "./components/TweetList.vue";
import SettingsModal from "./components/SettingsModal.vue";
import { ref } from "vue";
import { Tweet } from "./types/Tweet";

const tweets = ref<Tweet[]>([
  { id: "1", text: "Hello, Vue 3!" },
  { id: "2", text: "Hello, Vite!" },
]);

const onSubmitForm = (tweet: string) => {
  tweets.value.push({ id: String(Math.random()), text: tweet });
};

const isModalOpen = ref(false);
const onClickSettings = () => {
  isModalOpen.value = true;
};
</script>

<template>
  <div class="container">
    <div class="header">
      <button @click="onClickSettings">Settings</button>
    </div>
    <Teleport to="body">
      <SettingsModal v-if="isModalOpen" />
    </Teleport>
    <TweetForm @submit="onSubmitForm" />
    <TweetList :tweets="tweets" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
}

.header {
  display: flex;
  justify-content: flex-end;
  padding: 1em;
  button {
    border-radius: 0.5em;
    background-color: #81d6ee;
    color: white;
    width: 120px;
    height: 50px;
    font-size: 1em;
  }
}
</style>

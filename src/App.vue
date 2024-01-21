<script setup lang="ts">
import TweetForm from "./components/TweetForm.vue";
import TweetList from "./components/TweetList.vue";
import SettingsModal from "./components/SettingsModal.vue";
import { provide, readonly, ref } from "vue";
import { Tweet } from "./types/Tweet";
import { updateUserNameKey, userNameKey } from "./key";

const tweets = ref<Tweet[]>([
  { id: "1", text: "Hello, Vue 3!", userName: "test" },
  { id: "2", text: "Hello, Vite!", userName: "test2" },
]);

const onSubmitForm = (tweet: string) => {
  tweets.value.push({
    id: String(Math.random()),
    text: tweet,
    userName: userName.value,
  });
};

const isModalOpen = ref(false);
const onClickSettings = () => {
  isModalOpen.value = true;
};

const onSubmitSettings = (userName: string) => {
  console.log(userName);
  isModalOpen.value = false;
};

const userName = ref("");

const updateUserName = (name: string) => {
  userName.value = name;
};
provide(userNameKey, readonly(userName));
provide(updateUserNameKey, updateUserName);
</script>

<template>
  <div class="container">
    <div class="header">
      <button @click="onClickSettings">Settings</button>
    </div>
    <Teleport to="body">
      <SettingsModal @submit="onSubmitSettings" v-if="isModalOpen" />
    </Teleport>
    {{ userName }}
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

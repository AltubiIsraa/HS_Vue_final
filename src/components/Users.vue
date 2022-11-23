<script setup>
import { ref, onErrorCaptured } from "vue";
import UserCardVue from "./UserCard.vue";
const SelectedUser = ref(null);
const response = ref({});

// adding delay

await new Promise((resolve) => {
  setTimeout(() => {
    resolve();
  }, 1000);
});

onErrorCaptured((err) => {
  // error processing
});

response.value = await (
  await fetch("https://jsonplaceholder.typicode.com/users/")
).json();
</script>

<template>
  <select v-model="SelectedUser">
    <option v-for="item in response" v-bind:key="item.id" :value="item">
      {{ item.name }}
    </option>
  </select>

  <p v-for="item in response" v-bind:key="item.id" :value="item">
    {{ item.name }}
  </p>

  <UserCardVue :user="SelectedUser">{{ item }}</UserCardVue>
</template>

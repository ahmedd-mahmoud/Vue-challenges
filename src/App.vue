<script setup>
import { ref } from "vue";

const user = ref({ username: "", password: "" });
const isActive = ref(true);
const statusText = ref("");

const handleSubmit = () => {
  console.log(user.value);
  statusText.value = user.value.password === "1234" ? "Thank You!" : "Fail :(";
  isActive.value = false;
};
</script>

<template>
  <form
    @submit.prevent="handleSubmit"
    v-if="isActive"
    class="w-80 h-80 bg-[#adadad] flex flex-col justify-center items-center"
  >
    <label class="pr-32 mb-2">Username</label>
    <input v-model="user.username" class="mb-5 w-52 h-6 px-2 rounded-xl" />
    <label class="pr-32 mb-2">Password</label>
    <input
      v-model="user.password"
      type="password"
      class="mb-5 w-52 h-6 px-2 rounded-xl"
    />
    <button class="rounded-3xl mt-4">OK</button>
  </form>
  <p v-else>{{ statusText }}</p>
</template>

<style scoped></style>

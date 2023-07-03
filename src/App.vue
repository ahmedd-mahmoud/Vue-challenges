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
  <form @submit.prevent="handleSubmit" v-if="isActive">
    <label>Username</label>
    <input v-model="user.username" />
    <label>Password</label>
    <input v-model="user.password" type="password" />
    <button>OK</button>
  </form>
  <p v-else>{{ statusText }}</p>
</template>

<style scoped>
form {
  width: 400px;
  height: 400px;
  background-color: #adadad;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
label {
  padding-right: 32%;
  margin-bottom: 5px;
}
input {
  margin-bottom: 20px;
  width: 200px;
  height: 20px;
  border-radius: 5px;
}
p {
  font-size: xx-large;
}
</style>

<script setup>
import { ref } from "vue";
import Box from "./components/Box.vue";

const score = ref(0);
// const timer = ref(10);
const isEnded = ref(false);
const position = ref({ top: "50%", left: "50%" });

const states = {
  score,
  isEnded,
  position,
};

const handleRestart = () => {
  position.value.left = "50%";
  position.value.top = "50%";
  score.value = 0;
  isEnded.value = false;
  // setTimer(10);
};
</script>

<template>
  <div class="title-div">
    <h1 class="title">Catch me if you can:</h1>
  </div>
  <div>
    <!-- <p class="timer">Timer: 00:{{ timer }}</p> -->
    <p class="score-text">Score: {{ score }}</p>
  </div>
  <Box v-bind="states" v-if="!isEnded" />
  <div v-else class="result">
    <h1 class="result-text">Thanks for playing!</h1>
    <div class="result-buttons">
      <button class="restart-button" @click="handleRestart">Try again</button>
    </div>
  </div>
</template>

<style scoped>
body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-weight: bold;
  background-color: rgb(231, 255, 252);
}

.title-div {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 63%;
}

.title {
  font-size: 30px;
  margin-left: 50px;
  color: darkblue;
}

.result {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

.result-text {
  font-size: 64px;
  color: red;
}

.result-buttons {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

.restart-button {
  font-size: 16px;
  font-weight: bold;
  padding: 8px 12px;
  background-color: rgb(20, 173, 20);
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.restart-button:hover {
  background-color: rgb(14, 128, 14);
}

.score-text {
  text-align: center;
  font-size: 32px;
  margin-top: 5px;
}
</style>

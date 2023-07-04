<script setup>
import { computed, ref } from "vue";
const props = defineProps({
  score: Object,
  isEnded: Object,
  position: Object,
  // timer: Number,
});

const buttonStatus = ref("initial");

//remaining random position, onclick
const handleButtonClick = () => {
  props.isEnded.value = false;
  if (buttonStatus.value === "initial") {
    buttonStatus.value = "playing";
  } else if (buttonStatus.value === "playing") {
    props.score.value += 1;
    // container width= 1000px, height= 400px, button width = 30px , height = 15 px
    props.position.value.left = Math.random() * 1000 + 0.5 * 30 + "px";
    props.position.value.top = Math.random() * 400 + 0.5 * 15 + "px";
    if (props.score.value > 4) {
      props.isEnded.value = true;
      buttonStatus.value = "initial";
    }
  }
};

const buttonStyle = computed(() => {
  return {
    top: props.position.value.top,
    left: props.position.value.left,
  };
});
</script>

<template>
  <button
    @click="handleButtonClick"
    class="random-button"
    :style="buttonStyle"
    v-if="!isEnded.value"
  >
    {{ buttonStatus === "initial" ? "Start Game" : "Catch Me!" }}
  </button>
</template>

<style scoped>
.random-button {
  position: absolute;
  font-size: 16px;
  font-weight: bold;
  padding: 8px 12px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transform: translate(-50%, -50%);
}

.random-button:hover {
  background-color: #0056b3;
}
</style>

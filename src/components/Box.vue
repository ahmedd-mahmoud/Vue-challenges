<script setup>
import RandomButton from "./RandomButton.vue";

const props = defineProps({
  score: Object,
  isEnded: Object,
  position: Object,
  //   timer: Number,
});
const states = {
  score: props.score,
  isEnded: props.isEnded,
  position: props.position,
};
</script>

<template>
  <div class="container">
    <random-button v-bind="states" />
  </div>
</template>

<style scoped>
.container {
  position: relative;
  width: 1000px;
  height: 60vh;
  border: 5px solid #066baa;
  margin: auto;
}
</style>

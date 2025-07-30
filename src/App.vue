<script setup>
import { ref } from 'vue';
import MainButton from './components/MainButton.vue';

// const disabled = ref(false);
// const toDisable = () => {
//   disabled.value = !disabled.value;
// };
const count = ref(0);

const increment = (counter) => {
  count.value = count.value + counter;
};
</script>

<template>
  <!-- <MainButton @click="toDisable" :disabled /> -->
  <button @click="(event) => console.log(event)" @mouseover="increment(10)">
    {{ count }}
  </button>

  <input @keyup.enter="() => console.log('Enter pressed')" placeholder="Press Enter" />
  <br />
  <br />
  <MainButton class="my-btn" @click="increment(1)" />
</template>

<style scoped></style>

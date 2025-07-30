<script setup>
import { ref } from 'vue';
import MainButton from './components/MainButton.vue';

const disabled = ref(false);
const toDisable = () => {
  disabled.value = !disabled.value;
};
</script>

<template>
  <MainButton @click="toDisable" :disabled />
</template>

<style scoped></style>

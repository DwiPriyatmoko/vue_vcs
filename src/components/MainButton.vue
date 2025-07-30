<script setup>
// defineOptions({
//   inheritAttrs: false,
// });

import { useAttrs } from 'vue';
const attrs = useAttrs();
console.log(attrs.class);

const { title, disabled } = defineProps({
  title: {
    type: String,
    default: 'Subscribe',
  },
  disabled: {
    type: Boolean,
    default: false,
  },
});

const disableStyle = '#ACACAC';
const enableStyle = '#fff';
</script>

<template>
  <button
    v-bind="$attrs"
    :disabled
    class="button"
    :class="{ disabled: disabled }"
    :style="{ color: disabled ? disableStyle : enableStyle }"
  >
    {{ title }}
  </button>
</template>

<style scoped>
.button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.button:hover:not(.disabled) {
  background-color: #0056b3;
}

.disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}
</style>

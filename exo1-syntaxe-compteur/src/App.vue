<template>
  <p>compteur : {{ count }}</p>
  <button type="button" @click="add">Incremente</button>
  <button type="button" @click="remove">Decremente</button>
</template>

<script setup>
import { ref } from "vue";
const count = ref(0);
const add = () => {
  count.value += 1;
};
const remove = () => {
  count.value -= 1;
};
</script>

<style scoped></style>

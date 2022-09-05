<template>
  <div class="container mx-auto">
    <h1 class="text-xl">Choose Type</h1>
    <div class="text-left flex flex-col">
      <template v-for="(item, index) in data">
        <Type :data="item" />
      </template>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Type from "./Type.vue";
const data = ref(null);
try {
  fetch("https://pokeapi.co/api/v2/type")
    .then((res) => res.json())
    .then((response) => (data.value = response.results));
} catch (error) {}
</script>

<style lang="scss" scoped></style>

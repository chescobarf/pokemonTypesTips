<template>
  <div
    class="text-left grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-6 gap-3 lg:gap-6"
  >
    <template v-for="item in cleanData">
      <Type :data="item" />
    </template>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Type from "./Type.vue";
const data = ref(null);
const cleanData = ref([]);
try {
  fetch("https://pokeapi.co/api/v2/type")
    .then((res) => res.json())
    .then((response) => (data.value = response.results))
    .then(() => cleanNoTypes());
} catch (error) {
  console.log(error);
}

const cleanNoTypes = () => {
  const arrayTypes = data.value;
  arrayTypes.map((type) => {
    if (type.name != "unknown" && type.name != "shadow") {
      cleanData.value.push(type);
    }
  });
};
</script>

<style lang="scss" scoped></style>

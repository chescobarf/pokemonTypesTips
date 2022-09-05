<template>
  <div>
    <div v-if="data">
      <h2>Doble Daño De:</h2>
      <template v-for="item in data.double_damage_from">
        <Type :data="item" />
      </template>

      <h2>Doble Daño Hacia:</h2>
      <template v-for="item in data.double_damage_to">
        <Type :data="item" />
      </template>

      <h2>Medio Daño De:</h2>
      <template v-for="item in data.half_damage_from">
        <Type :data="item" />
      </template>
      <h2>Medio Daño Hacia:</h2>
      <template v-for="item in data.half_damage_to">
        <Type :data="item" />
      </template>

      <h2>Inmune a:</h2>
      <template v-for="item in data.no_damage_from">
        <Type :data="item" />
      </template>

      <h2>No le hace daño a:</h2>
      <template v-for="item in data.no_damage_to">
        <Type :data="item" />
      </template>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Type from "../components/TypeList/Type.vue";
import { useRoute } from "vue-router";
const data = ref(null);
const route = useRoute();
try {
  const typeID = route.params.name;
  fetch("https://pokeapi.co/api/v2/type/" + typeID)
    .then((res) => res.json())
    .then((response) => {
      data.value = response.damage_relations;
    });
} catch (error) {
  console.log(error);
}
</script>

<style lang="scss" scoped></style>

<template>
  <main class="container px-4 sm:mx-auto">
    <div v-if="data">
      <span class="text-lg">Doble Daño De:</span>
      <LayoutTypes>
        <template v-for="item in data.double_damage_from">
          <Type :data="item" />
        </template>
      </LayoutTypes>

      <span class="text-lg">Doble Daño Hacia:</span>
      <LayoutTypes>
        <template v-for="item in data.double_damage_to">
          <Type :data="item" />
        </template>
      </LayoutTypes>

      <span class="text-lg">Medio Daño De:</span>
      <LayoutTypes>
        <template v-for="item in data.half_damage_from">
          <Type :data="item" />
        </template>
      </LayoutTypes>

      <span class="text-lg">Medio Daño Hacia:</span>
      <LayoutTypes>
        <template v-for="item in data.half_damage_to">
          <Type :data="item" />
        </template>
      </LayoutTypes>

      <span class="text-lg">Inmune a:</span>
      <LayoutTypes>
        <template v-for="item in data.no_damage_from">
          <Type :data="item" />
        </template>
      </LayoutTypes>

      <span class="text-lg">No le hace daño a:</span>
      <LayoutTypes>
        <template v-for="item in data.no_damage_to">
          <Type :data="item" />
        </template>
      </LayoutTypes>
    </div>
  </main>
</template>

<script setup>
import { ref } from "vue";
import Type from "../components/TypeList/Type.vue";
import { useRoute } from "vue-router";
import LayoutTypes from "../layouts/LayoutTypes.vue";
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

<template>
  <main class="container px-4 sm:mx-auto">
    <h1 class="text-2xl capitalize mb-5">{{ route.params.name }} Type</h1>
    <div v-if="data" class="grid md:grid-cols-2">
      <div class="atacking">
        <h2 class="text-2xl mb-3">Atacando</h2>
        <template v-if="data.double_damage_to.length > 0">
          <div class="text-lg mb-4">
            <span class="bg-green-700 text-white p-2 rounded-full">2x</span>
            Doble Daño Hacia:
          </div>
          <LayoutTypes>
            <template v-for="item in data.double_damage_to">
              <Type :data="item" />
            </template>
          </LayoutTypes>
        </template>
        <template v-if="data.half_damage_to.length > 0">
          <div class="text-lg mb-4">
            <span class="bg-red-700 text-white p-2 rounded-full">½x</span>
            Medio Daño Hacia:
          </div>
          <LayoutTypes>
            <template v-for="item in data.half_damage_to">
              <Type :data="item" />
            </template>
          </LayoutTypes>
        </template>

        <template v-if="data.no_damage_to.length > 0">
          <div class="text-lg mb-4">
            <span class="bg-black text-white p-2 rounded-full">0x</span>
            No le hace daño a:
          </div>
          <LayoutTypes>
            <template v-for="item in data.no_damage_to">
              <Type :data="item" />
            </template>
          </LayoutTypes>
        </template>
      </div>
      <div class="defending">
        <h2 class="text-2xl mb-3">Defendiendo</h2>
        <template v-if="data.no_damage_from.length > 0">
          <div class="text-lg mb-4">
            <span class="bg-black text-white p-2 rounded-full">0x</span>
            Inmune a:
          </div>
          <LayoutTypes>
            <template v-for="item in data.no_damage_from">
              <Type :data="item" />
            </template>
          </LayoutTypes>
        </template>
        <template v-if="data.half_damage_from.length > 0">
          <div class="text-lg mb-4">
            <span class="bg-red-700 text-white p-2 rounded-full">½x</span>
            Medio Daño De:
          </div>
          <LayoutTypes>
            <template v-for="item in data.half_damage_from">
              <Type :data="item" />
            </template>
          </LayoutTypes>
        </template>
        <template v-if="data.double_damage_from.length > 0">
          <div class="text-lg mb-4">
            <span class="bg-green-700 text-white p-2 rounded-full">2x</span>
            Doble Daño De:
          </div>
          <LayoutTypes>
            <template v-for="item in data.double_damage_from">
              <Type :data="item" />
            </template>
          </LayoutTypes>
        </template>
      </div>
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

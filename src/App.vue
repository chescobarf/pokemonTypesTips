<script setup>
import { RouterLink, RouterView } from "vue-router";
import { setColorsVariables } from "./helpers/setTypesColors";
setColorsVariables();
</script>

<template>
  <header>
    <nav class="py-2">
      <RouterLink to="/" class="cursor-pointer"
        ><img
          src="./assets/logo.png"
          alt="LogoPokemonTypesTips"
          class="w-96 mx-auto"
      /></RouterLink>
    </nav>
  </header>
  <RouterView :key="$route.fullPath" />
</template>

<style></style>

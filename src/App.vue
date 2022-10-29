<script setup>
import { RouterLink, RouterView } from "vue-router";
import { setColorsVariables } from "./helpers/setTypesColors";
setColorsVariables();
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
    </nav>
  </header>
  <RouterView :key="$route.fullPath" />
</template>

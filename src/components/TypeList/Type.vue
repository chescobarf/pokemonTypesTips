<template>
  <router-link
    :to="url"
    class="capitalize mb-3 py-1 px-3 rounded cursor-pointer"
    :class="data.name"
  >
    {{ data.name }}
  </router-link>
</template>

<script setup>
import { computed } from "vue";
const props = defineProps({
  data: Object,
});
const url = computed(() => "/type/" + props.data.name);
</script>

<style>
.normal {
  background-color: beige;
}
.fighting {
  background-color: orangered;
}
.flying {
  background-color: lavender;
}
.poison {
  background-color: blueviolet;
}
.ground {
  background-color: darkkhaki;
}
.rock {
  background-color: brown;
}
.bug {
  background-color: greenyellow;
}
.ghost {
  background-color: darkslateblue;
}
.steel {
  background-color: silver;
}
.fire {
  background-color: red;
}
.water {
  background-color: blue;
}
.grass {
  background-color: green;
}
.electric {
  background-color: yellow;
}
.psychic {
  background-color: pink;
}
.ice {
  background-color: aqua;
}
.dragon {
  background-color: midnightblue;
  color: white;
}
.dark {
  background-color: black;
  color: white;
}
.fairy {
  background-color: magenta;
}
.unknown {
  background-color: whitesmoke;
}
.shadow {
  background-color: indigo;
  color: red;
}
</style>

<template>
  <router-link
    :to="url"
    class="type capitalize mb-3 p-4 rounded-xl text-center grid place-content-center place-items-center gap-2 min-w-[120px] min-h-[120px]"
    :class="data.name"
  >
    <img
      :src="pathIcon(data.name)"
      :alt="data.name"
      class="w-8 h-8 md:w-12 md:h-12 lg:w-18 lg:h-18"
    />
    <span class="text-white">{{ data.name }}</span>
  </router-link>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  data: Object,
});
const url = computed(() => "/type/" + props.data.name);

const pathIcon = (type) => {
  return `./src/assets/icons/${type}.svg`;
};
</script>

<style scoped>
.type:hover {
  filter: saturate(200%);
  cursor: pointer;
}
</style>

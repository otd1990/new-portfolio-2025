<script setup>
import { computed } from "vue";

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
});

const icons = import.meta.glob("/src/assets/images/icons/*.svg", {
  eager: true,
});

const icon = computed(() => {
  return icons[`/src/assets/images/icons/${props.name}.svg`]?.default;
});
</script>

<template>
  <component :is="icon" class="fill-current" />
</template>

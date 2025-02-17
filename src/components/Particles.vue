<script setup>
import { onMounted } from "vue";

const particlesLoaded = async (container) => {
  console.log("Particles container loaded", container);
};

onMounted(() => {
  console.log("Mounted");
});
</script>

<template>
  <vue-particles
    id="tsparticles"
    @particles-loaded="particlesLoaded"
    :options="{
      particles: {
        number: {
          value: 150,
        },
        size: {
          value: 1,
        },
        move: {
          enable: true,
          speed: 2, // Speed of the particles
          direction: 'bottom-right', // Direction of movement (diagonal)
          straight: true, // Keep particles moving in straight lines
          outModes: {
            default: 'out', // Particles disappear when they leave the screen
          },
        },
        links: {
          enable: false,
          distance: 80,
          color: '#ffffff',
          opacity: 0.1,
          width: 2,
        },
      },
    }"
  />
</template>

<style scoped>
.particles {
  width: 100vw;
  height: 100vh;
  z-index: -1;
  background: #042731;
}
</style>

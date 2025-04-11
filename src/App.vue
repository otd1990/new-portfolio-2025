<script setup>
import { ref } from "vue";
import Particles from "./components/Particles.vue";
import Intro from "./components/Intro.vue";
import Expertise from "./components/Expertise.vue";
import MyWork from "./components/MyWork.vue";
import ProfessionalExperience from "./components/ProfessionalExperience.vue";

const main = ref();

const handleScroll = () => {
  main.value.scrollIntoView({
    behavior: "smooth",
    block: "end",
    inline: "nearest",
  });
};
</script>

<template>
  <div id="app">
    <section class="canvas-bg">
      <article class="hero">
        <Particles />
        <Intro @scroll-to-main="handleScroll" />
      </article>
      <article id="main" ref="main">
        <Expertise />
        <section class="dark-bg">
          <MyWork />
        </section>
        <section class="dark-bg margin-0">
          <ProfessionalExperience />
        </section>
      </article>
    </section>
  </div>
</template>

<style scoped>
#main {
  height: 100dvh;
}

.canvas-bg {
  background: linear-gradient(#042731 5%, #1d1d1d 95%);
}

.dark-bg {
  background-color: #1d1d1d;
  position: relative;
  margin-top: 2rem;
}

.container {
  padding: 2rem;
  margin: 0 auto;
  max-width: 1400px;
}
</style>

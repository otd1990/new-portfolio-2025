<script setup>
import { ref } from "vue";
import Particles from "./components/Particles.vue";
import Intro from "./components/Intro.vue";
import Expertise from "./components/Expertise.vue";
import MyWork from "./components/MyWork.vue";

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
  <div id="app" class="container">
    <article class="hero">
      <Particles />
      <Intro @scroll-to-main="handleScroll" />
    </article>
    <article id="main" ref="main">
      <Expertise />
      <MyWork />
    </article>
  </div>
</template>

<style scoped>
.hero {
  height: 100dvh;
}

article {
  height: 100dvh;
}

.container {
  padding: 2rem;
  margin: 0 auto;
  max-width: 1400px;
}
</style>

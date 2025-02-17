<script setup lang="ts">
import Icon from "./Icon.vue";

defineEmits<{ (e: "scrollToMain"): void }>();
</script>

<template>
  <section class="intro">
    <article class="intro__upper">
      <h1>OLIVER DYER</h1>
      <span class="intro-skills">Frontend Developer, UI Engineer</span>
    </article>
    <button class="intro__button button--reset" @click="$emit('scrollToMain')">
      <span class="sr-only">Go to main content</span>
      <div class="intro__button--icon"><Icon name="down-arrow" /></div>
    </button>
  </section>
</template>

<style scoped>
.intro {
  position: relative;
  color: #fff;
  text-align: center;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  height: 75%;
}

.intro-skills {
  font-size: 1.2rem;
  text-transform: uppercase;
  letter-spacing: 2px;
  animation: slideUp 0.7s 0.3s both;
  display: block;
}

.intro__button {
  height: 4rem;
  width: 2.5rem;

  border: 2px solid white;
  border-radius: 50px;

  position: absolute;
  bottom: 3rem;
}

.intro__button--icon {
  margin: auto;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 10px;

  color: #66d9ed;

  animation: smoothBounce 1s 1s infinite;
}

@keyframes slideUp {
  0% {
    opacity: 0;
    transform: translateY(40px);
  }

  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes smoothBounce {
  0% {
    transform: translate(-50%, 5px);
  }
  50% {
    transform: translate(-50%, 10px);
  }
  100% {
    transform: translate(-50%, 5px);
  }
}
</style>

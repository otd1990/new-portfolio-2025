<script setup lang="ts">
import { DotLottieVue } from "@lottiefiles/dotlottie-vue";
import Icon from "./Icon.vue";
</script>

<template>
  <section class="my-work section-padding">
    <div class="my-work__intro">
      <h2 class="h1">My<br />Work</h2>
      <section class="my-work__intro-text">
        <div>
          <p>
            Personal projects that have helped me build, develop and maintain my
            current skills.
          </p>
          <p>
            I am always on the look out for fun ways to challenge myself and
            create things from scratch
          </p>
        </div>
      </section>
    </div>
    <aside class="my-work__image">
      <Icon name="work-animation" />
    </aside>
  </section>
</template>

<style scoped>
.my-work {
  display: flex;
  gap: 1rem;

  > div {
    flex: 1;
  }

  > aside {
    flex: 2;

    > svg {
      margin: 0 auto;
      display: block;
    }
  }
}
.my-work__intro-text {
  color: #fff;
}
</style>

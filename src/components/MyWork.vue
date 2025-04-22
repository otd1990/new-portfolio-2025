<script setup lang="ts">
import Icon from "./Icon.vue";
import WorkItems from "./WorkItems.vue";
</script>

<template>
  <section class="my-work section-padding">
    <div class="my-work__intro">
      <h2 class="h1">
        <span class="my-work__heading-first-word">My</span> Work
      </h2>
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
  <section class="my-work__work-container">
    <WorkItems />
  </section>
</template>

<style scoped>
.my-work {
  display: flex;
  gap: 1rem;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  flex-wrap: wrap;
}

.my-work__intro {
  flex: 1;
}

.my-work__heading-first-word {
  font-weight: inherit;
}

.my-work__heading-first-word::after {
  content: "\A";
  white-space: pre;
}

.my-work__image {
  flex: 0;
}

.my-work__image svg {
  margin: 0 auto;
  display: block;
}

.my-work__intro-text {
  color: #fff;
}

.my-work__intro-text p {
  font-family: "Roboto Mono", serif;
  line-height: 1.75rem;
}

.my-work__work-container {
  padding-bottom: 8rem;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

@media (max-width: 768px) {
  .my-work__intro,
  .my-work__image {
    flex: 1 0 100%;
  }

  .my-work__image svg {
    height: auto !important;
    width: 100% !important;
  }

  .my-work__intro .h1 {
    text-align: center;
  }

  .my-work__heading-first-word::after {
    content: "";
    white-space: initial;
  }
}
</style>

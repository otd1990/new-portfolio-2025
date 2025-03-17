<script setup lang="ts">
import Icon from "./Icon.vue";
import WorkItems from "./WorkItems.vue";
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

  > div {
    flex: 1;
  }

  > aside {
    flex: 0;

    > svg {
      margin: 0 auto;
      display: block;
    }
  }
}
.my-work__intro-text {
  color: #fff;
}

.my-work__work-container {
  padding-bottom: 8rem;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}
</style>

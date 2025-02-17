<script setup lang="ts">
const expertise = [
  {
    id: 1,
    title: "Web & Software\nDevelopment",
    icon: "computer-logo",
    description:
      "Experienced in developing front end for both websites and software.",
  },
  {
    id: 2,
    title: "Frontend Development",
    icon: "vue-logo",
    description:
      "Passionate about development. Commercial experience with; Vue, React, Nuxt frameworks as well as vanilla JS.",
  },
  {
    id: 3,
    title: "Design Interpretation",
    icon: "figma-logo",
    description: "Able to turn designs into reality using Figma, SCSS & HTML",
  },
];
</script>

<template>
  <section class="expertise section-padding">
    <h2 class="h1">My Expertise</h2>
    <article class="expertise__boxes">
      <section
        v-for="exp in expertise"
        :key="exp.id"
        class="expertise__box-inner"
      >
        <div class="expertise__box-upper">
          <Icon :name="exp.icon" />
          <h4 class="expertise__box-heading">{{ exp.title }}</h4>
        </div>
        <p class="expertise__box-desc">
          <span class="expertise__box-desc-text">{{ exp.description }}</span>
        </p>
      </section>
    </article>
  </section>
</template>

<style scoped>
h2 {
  text-align: center;
}

.expertise__boxes {
  display: flex;
  justify-content: center;
}

.expertise__box-inner {
  border: 1px solid #fff;
  padding: 1.5rem;
  color: #fff;
  flex: 1;
}

.expertise__box-upper {
  display: flex;
  align-items: center;
  gap: 1rem;
  color: inherit;

  > svg {
    height: 2rem;
    width: 4rem;
  }
}

.expertise__box-heading {
  font-size: 1.25rem;
}

.expertise__box-desc {
  border-left: 1px solid rgba(255, 255, 255, 0.25);
}

.expertise__box-desc-text {
  padding-left: 1rem;
  display: block;
}
</style>

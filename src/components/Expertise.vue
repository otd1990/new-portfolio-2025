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
          <div class="expertise__box-icon-container">
            <Icon :name="exp.icon" />
          </div>
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

/* .expertise {
  height: 100dvh;
} */

.expertise__boxes {
  display: flex;
  justify-content: center;
  margin: 0 0.5rem;
  max-width: 1200px;
  margin: 0 auto;
  flex-wrap: wrap;
}

.expertise__box-inner {
  border: 1px solid #fff;
  padding: 1.5rem;
  color: #fff;
  flex: 0 0 auto;
  width: 33.333333333%;
}

.expertise__box-upper {
  display: flex;
  align-items: center;
  color: inherit;
}

.expertise__box-icon-container {
  min-height: 2rem;
  min-width: 2rem;
  margin-right: 0.75rem;

  > svg {
    height: 2rem;
    width: 2rem;
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

@media (max-width: 1400px) {
  .expertise__boxes {
    max-width: 900px;
    margin: 0 auto;
  }
  .expertise__box-inner {
    width: 50%;
  }
}

@media (max-width: 900px) {
  .expertise__boxes {
    max-width: 80%;
    margin: 0 auto;
    padding: 0 1rem;
  }
  .expertise__box-inner {
    width: 100%;
    margin-bottom: 1rem;
  }
}

@media (max-width: 768px) {
  .expertise__boxes {
    max-width: 100%;
  }
  .expertise__box-inner {
    width: 100%;
    margin-bottom: 1rem;
  }
}
</style>

<template>
  <article class="work-item__wrapper">
    <section class="work-item__filter">
      <ul class="work-item__filter-list">
        <li
          v-for="(lang, index) in primaryLangs"
          :key="`${lang}-${index}`"
          class="work-item__filter-list-item"
        >
          <button
            @click="setProjectType(lang)"
            class="work-item__filter-list-btn button--reset poppins-extralight"
            :class="{
              'work-item__filter-list-btn--active':
                lang.toLocaleLowerCase() === projectType,
            }"
          >
            {{ lang }} <sup>0{{ index + 1 }}. </sup>
          </button>
        </li>
      </ul>
    </section>
    <section class="work-item__gallery">
      <article
        v-for="(project, index) in filteredProjects"
        :key="`${project}${project.id}-${index}`"
        class="work-item__gallery-item"
      >
        <div
          class="work-item__gallery-item-image"
          :style="{
            backgroundImage: `url('/project-images/${project.imageName}')`,
          }"
        ></div>
        <div class="work-item__gallery-name">
          <div class="work-item__gallery-name-container">
            <h4>{{ project.name }}</h4>
            <p class="poppins-regular light-colour">
              {{ project.description }}
            </p>
            <section class="work-item__built-with flex-center-between">
              <p>Built With</p>
              <div class="work-item__gallery-lang-icon">
                <Icon
                  v-for="(item, idx) in project.builtWith"
                  :key="`${item}-${index}-${idx}`"
                  :name="item"
                />
              </div>
            </section>
          </div>
          <a
            class="btn btn-primary work-item__btn"
            :href="`${project.url}`"
            target="blank"
            rel="noopener noreferrer"
          >
            <div>{{ project.isDeployed ? "Visit Site" : "Go to project" }}</div>
            <span class="work-item__icon"><Icon name="down-arrow" /></span
          ></a>
        </div>
      </article>
    </section>
  </article>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import Icon from "./Icon.vue";

const primaryLangs = ["All", "Vue/Nuxt", "React", "JavaScript", "JQuery"];

const projects = [
  {
    id: 1,
    name: "AI Chatbots",
    description:
      "A lightly styled look into how Vue & Node can be used to work with the OpenAI API",
    builtWith: ["vue", "nodejs", "css"],
    imageName: "chat-bots.png",
    url: "https://github.com/otd1990/ai-bots",
    backgroundColour: "#39a7ff",
    primaryLang: "vue/nuxt",
    isDeployed: false,
  },
  {
    id: 2,
    name: "Sandra Plumb Books",
    description:
      "A website used display books written by an independant author. This site is built with a CMS meaning the creator can control their work",
    builtWith: ["nuxt", "scss", "supabase"],
    url: "https://github.com/otd1990/Sandra-Books",
    imageName: "sandra-pumb-books.png",
    backgroundColour: "#fbf8f2",
    primaryLang: "vue/nuxt",
    isDeployed: false,
  },
  {
    id: 3,
    name: "First Dance Thame",
    description: "A website for a dance teacher",
    builtWith: ["js", "css", "bootstrap"],
    url: "https://firstdanceclasses.co.uk/",
    imageName: "first-dance.png",
    backgroundColour: "#333",
    primaryLang: "javascript",
    isDeployed: true,
  },
  {
    id: 4,
    name: "Nicola Evans Fine Art",
    description: "A website for a freelance artist to showcase their work",
    builtWith: ["jquery", "scss", "bootstrap"],
    url: "https://nicolaevansfineart.com/",
    imageName: "nic-f-a.png",
    backgroundColour: "#7D7C7C",
    primaryLang: "jquery",
    isDeployed: true,
  },
  {
    id: 5,
    name: "Portfolio v1",
    description: "My first portfolio",
    builtWith: ["react", "js", "scss", "bootstrap"],
    url: "https://odyer755.github.io/",
    imageName: "old-profile.png",
    backgroundColour: "#006a71",
    primaryLang: "react",
    isDeployed: true,
  },
  {
    id: 6,
    name: "Gallery App v1",
    description:
      "An app that displays a variety of different famous artworks in an automated gallery",
    builtWith: ["vue", "css"],
    // url: "https://otd1990.github.io/gallery-app/",
    url: "https://otd1990.github.io/gallery-app/",
    imageName: "gallery-app.png",
    backgroundColour: "#070F2B",
    primaryLang: "vue/nuxt",
    isDeployed: true,
  },
];

const projectType = ref(primaryLangs[0].toLocaleLowerCase());

const setProjectType = (lang: string): void => {
  console.log(lang);
  // loop through projects, show projects that match item selected in filter
  projectType.value = lang.toLocaleLowerCase();
};

const filteredProjects = computed(() => {
  if (projectType.value === "all") {
    return projects;
  }

  return projects.filter(
    (project) => project.primaryLang === projectType.value
  );
});
</script>

<style scoped>
.work-item__filter-list {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.work-item__filter-list-item {
  display: flex;
  align-items: center;
}

.work-item__filter-list-item:not(:last-child):after {
  content: "/ ";
  color: #fff;
  display: inline-block;
  padding: 0 1.5rem;
}

.work-item__filter-list-btn {
  color: #fff;
  font-size: 1rem;
  letter-spacing: 1px;
  cursor: pointer;

  > sup {
    position: relative;
    top: -2.75pt;
    font-size: 0.65rem;
  }
}

.work-item__filter-list-btn--active {
  color: #66d9ed;
}

.work-item__gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 1.5rem;
  grid-row-gap: 1.5rem;
}

.work-item__gallery-item {
  max-width: 25.714rem;
  width: 100%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.work-item__gallery-item-image {
  max-width: 100%;
  width: 100%;
  overflow: hidden;
  height: 15.7rem;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;

  > img {
    width: 100%;
    object-fit: fill;
  }
}

.work-item__gallery-name {
  flex: 1;
  background-color: #333;
  padding: 1rem 0.75rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.work-item__gallery-name-container {
  margin-bottom: 1rem;
  > h4 {
    font-size: 1.2rem;
  }
}

.work-item__btn {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 12rem;
  margin-left: auto;

  > span {
    display: block;
    transform: rotate(-90deg);
  }
}

.work-item__gallery-lang-icon {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  justify-content: flex-end;
  padding: 0.75rem;

  > svg {
    height: 1rem;
    width: 1rem;
  }
}

.work-item__built-with {
  > p {
    color: #fff;
    font-size: 0.7rem;
  }
}

@media (max-width: 900px) {
  .work-item__gallery {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 800px) {
  .work-item__filter-list-item:not(:last-child)::after {
    padding: 0 0.5rem;
  }
}

@media (max-width: 610px) {
  .work-item__gallery {
    grid-template-columns: repeat(1, 1fr);
  }

  .work-item__filter-list {
    flex-wrap: wrap;
    justify-content: center;
  }
}
</style>

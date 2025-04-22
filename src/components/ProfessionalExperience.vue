<template>
  <article class="professional-experience container">
    <h2 class="section-heading">Professional<br />Experience</h2>
    <section class="professional-experience__accordions">
      <Accordion
        v-for="(exp, index) in experience"
        ref="accordions"
        :key="`${index}-${exp.title}`"
        :title="`${exp.title} @ ${exp.company}`"
        :title-sup="exp.yearsWorked"
        :accordion-no="exp.id"
        :isOpen="isOpenStates[index]"
        @click="() => handleToggle(index)"
      >
        <template #body>
          <div v-html="body[index]?.body"></div>
        </template>
      </Accordion>
    </section>
  </article>
</template>

<script setup lang="ts">
import { ref, useTemplateRef, nextTick } from "vue";
import Accordion from "./Utilities/Accordion.vue";

const accordionRefs = useTemplateRef("accordions");

const experience = [
  {
    id: 1,
    title: "UI Developer",
    company: "Dominos UK & Ireland",
    yearsWorked: "2022 - Present",
    jd: "",
  },
  {
    id: 2,
    title: "Frontend Developer",
    company: "Civil Service",
    yearsWorked: "2021 - 2022",
    jd: "",
  },
  {
    id: 3,
    title: "Frontend Developer",
    company: "Fusemetrix LTD",
    yearsWorked: "2019 - 2021",
    jd: "",
  },
  {
    id: 4,
    title: "Fieldwork Technology Programmer",
    company: "MaritzCX",
    yearsWorked: "2022 - Present",
    jd: "",
  },
];

const body = [
  {
    body: `
      <h4 class="professional-experience__heading">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="256" height="256" viewBox="0 0 256 256" xml:space="preserve">
          <g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)">
            <path d="M 45 0 C 25.463 0 9.625 15.838 9.625 35.375 c 0 8.722 3.171 16.693 8.404 22.861 L 45 90 l 26.97 -31.765 c 5.233 -6.167 8.404 -14.139 8.404 -22.861 C 80.375 15.838 64.537 0 45 0 z M 45 48.705 c -8.035 0 -14.548 -6.513 -14.548 -14.548 c 0 -8.035 6.513 -14.548 14.548 -14.548 s 14.548 6.513 14.548 14.548 C 59.548 42.192 53.035 48.705 45 48.705 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round"/>
          </g>
        </svg>
        <span class="professional-experience__heading-text">Remote</span>
      </h4>
      <p>
        Took on a major role in upgrading the component library from Vue 2
        to Vue 2.7 and then to Vue 3. Improving accessibility and
        scalability along the way. Assisted in implementing components into
        the website and also upgrading the website from Nuxt 2 to Nuxt 3.
      </p>
      <div class="professional-experience__pill-container">      
        <span class="professional-experience__pill">Vue</span>
        <span class="professional-experience__pill">Pinia</span>
        <span class="professional-experience__pill">SCSS</span>
        <span class="professional-experience__pill">Nuxt</span>
        <span class="professional-experience__pill">API's</span>
      </div>
      `,
  },
  {
    body: `
      <h4 class="professional-experience__heading">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="256" height="256" viewBox="0 0 256 256" xml:space="preserve">
          <g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)">
            <path d="M 45 0 C 25.463 0 9.625 15.838 9.625 35.375 c 0 8.722 3.171 16.693 8.404 22.861 L 45 90 l 26.97 -31.765 c 5.233 -6.167 8.404 -14.139 8.404 -22.861 C 80.375 15.838 64.537 0 45 0 z M 45 48.705 c -8.035 0 -14.548 -6.513 -14.548 -14.548 c 0 -8.035 6.513 -14.548 14.548 -14.548 s 14.548 6.513 14.548 14.548 C 59.548 42.192 53.035 48.705 45 48.705 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round"/>
          </g>
        </svg>
        <span class="professional-experience__heading-text">London, UK</span>
      </h4>
      <p>
        Worked on creating business critical web based apps for a multiple government departments. Worked on both designing and creating the frontend of these apps - focusing on usability and accessibility.
      </p>
      <p>
        Maintained existing projects working with different teams to ensure work was done in an efficient manner.
      </p>
      <div class="professional-experience__pill-container">      
        <span class="professional-experience__pill">React</span>
        <span class="professional-experience__pill">Redux</span>
        <span class="professional-experience__pill">SCSS</span>
        <span class="professional-experience__pill">GoLang</span>
        <span class="professional-experience__pill">DevOps</span>
        <span class="professional-experience__pill">API's</span>
      </div>
      `,
  },
  {
    body: `
      <h4 class="professional-experience__heading">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="256" height="256" viewBox="0 0 256 256" xml:space="preserve">
          <g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)">
            <path d="M 45 0 C 25.463 0 9.625 15.838 9.625 35.375 c 0 8.722 3.171 16.693 8.404 22.861 L 45 90 l 26.97 -31.765 c 5.233 -6.167 8.404 -14.139 8.404 -22.861 C 80.375 15.838 64.537 0 45 0 z M 45 48.705 c -8.035 0 -14.548 -6.513 -14.548 -14.548 c 0 -8.035 6.513 -14.548 14.548 -14.548 s 14.548 6.513 14.548 14.548 C 59.548 42.192 53.035 48.705 45 48.705 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round"/>
          </g>
        </svg>
        <span class="professional-experience__heading-text">Milton Keynes, UK</span>
      </h4>
      <p>
        Built and maintained websites for clients in a variety of industries. Also worked on updating the business management software the company sold, modernising it's look.
      </p>
      <p>
        Met with clients to dicuss designs and work with them to draw up timelines ensuring that work was prioritised correctly. I would also help out with customer support if it was needed. 
      </p>
      <div class="professional-experience__pill-container">      
        <span class="professional-experience__pill">Javascript</span>
        <span class="professional-experience__pill">JQuery</span>
        <span class="professional-experience__pill">HTML</span>
        <span class="professional-experience__pill">CSS</span>
        <span class="professional-experience__pill">API's</span>
      </div>
      `,
  },
  {
    body: `
      <h4 class="professional-experience__heading">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="256" height="256" viewBox="0 0 256 256" xml:space="preserve">
          <g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)">
            <path d="M 45 0 C 25.463 0 9.625 15.838 9.625 35.375 c 0 8.722 3.171 16.693 8.404 22.861 L 45 90 l 26.97 -31.765 c 5.233 -6.167 8.404 -14.139 8.404 -22.861 C 80.375 15.838 64.537 0 45 0 z M 45 48.705 c -8.035 0 -14.548 -6.513 -14.548 -14.548 c 0 -8.035 6.513 -14.548 14.548 -14.548 s 14.548 6.513 14.548 14.548 C 59.548 42.192 53.035 48.705 45 48.705 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: currentColor; fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round"/>
          </g>
        </svg>
        <span class="professional-experience__heading-text">High Wycombe, UK</span>
      </h4>
      <p>
        created and maintain web and telephone based questionnaires across a number of different projects in a variety of industries. Writing cshell scripts to load and collect customer data and convert that data in formats that could be used for analysis and presentations.
      </p>
      <p>
        Working in an agile environment to maintain project timelines and allocate resources to where they are needed.
      </p>
      <div class="professional-experience__pill-container">      
        <span class="professional-experience__pill">PHP</span>
        <span class="professional-experience__pill">JavaScript</span>
        <span class="professional-experience__pill">SQL</span>
        <span class="professional-experience__pill">HTML</span>
        <span class="professional-experience__pill">CSS</span>
      </div>
      `,
  },
];

const isOpenStates = ref(new Array(experience.length).fill(false));

const handleToggle = async (index) => {
  isOpenStates.value[index] = !isOpenStates.value[index];

  await nextTick(); // Wait for state update

  accordionRefs.value?.forEach((accordion, i) => {
    if (i !== index) {
      isOpenStates.value[i] = false;
    }
    accordion?.toggleAccordion(isOpenStates.value[i]);
  });
};
</script>

<style>
.professional-experience {
  padding: 4rem 2rem;
}

.section-heading {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 2rem;
}

.professional-experience__accordions {
  max-width: 1200px;
  width: 100%;
  padding: 0 2rem;
  margin: 0 auto;
}

.professional-experience__heading {
  display: flex;
  gap: 4px;
  margin-bottom: 0.25rem;
}

.professional-experience__heading svg {
  height: auto;
  width: 1rem;
  color: #b7f;
}

.professional-experience__heading-text {
  color: rgba(255, 255, 255, 0.75);
  letter-spacing: normal;
  font-size: 1rem;
}

.professional-experience__pill-container {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: 0.5rem;

  margin-top: 1rem;
}

.professional-experience__pill {
  background-color: #740bdc;
  opacity: 0.8;
  padding: 0.5rem 0.75rem;
  font-size: 0.75rem;
  border-radius: 2rem;
}

@media (max-width: 1200px) {
  .professional-experience__accordions {
    padding: 0;
  }
}
</style>

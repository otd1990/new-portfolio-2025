<template>
  <article class="professional-experience">
    <h2 class="section-heading">Professional<br />Experience</h2>
    <section class="professional-experience__accordions">
      <Accordion
        v-for="(exp, index) in experience"
        ref="accordions"
        :key="`${index}-${exp.title}`"
        :title="exp.title"
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
      <h4>Dominos UK & Ireland</h4>
      <h4>Remote</h4>
      <p>
        Took on a major role in upgrading the component library from Vue 2
        to Vue 2.7 and then to Vue 3. Improving accessibility and
        scalability along the way. Assisted in implementing components into
        the website and also upgrading the website from Nuxt 2 to Nuxt 3.
      </p>`,
  },
  {
    body: `
      <h4>Civil Service</h4>
      <h4>London, UK</h4>
      <p>
        Worked on multiple projects for the UK government, improving frontend
        accessibility and performance for public sector applications.
      </p>`,
  },
  {
    body: `
      <h4>Fusemetrix LTD</h4>
      <h4>Milton Keynes, UK</h4>
      <p>
        Developed and maintained frontend applications using Vue.js and
        ensured smooth integration with backend APIs.
      </p>`,
  },
  {
    body: `
      <h4>MaritzCX</h4>
      <h4>Remote</h4>
      <p>
        Built and optimized survey-based applications using modern frontend
        technologies to enhance user engagement.
      </p>`,
  },
];

const isOpenStates = ref(new Array(experience.length).fill(false));

const handleToggle = async (index) => {
  isOpenStates.value[index] = !isOpenStates.value[index];

  await nextTick(); // Wait for state update

  accordionRefs.value.forEach((accordion, i) => {
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
</style>

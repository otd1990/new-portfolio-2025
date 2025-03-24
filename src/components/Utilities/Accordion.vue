<template>
  <section class="accordion">
    <label class="accordion__label" :for="`accordionRadio-${accordionNo}`">
      <div>{{ title }}</div>
    </label>
    <input
      :id="`accordionRadio-${accordionNo}`"
      type="radio"
      radiogroup="accordion-radio"
      name="accordion-radio"
      class="accordion__radio"
    />

    <section class="accordion__body">
      <slot name="body"></slot>
    </section>
  </section>
</template>

<script setup lang="ts">
interface IAccordionProps {
  accordionNo: number;
  title: string;
  titleSup?: string;
  body?: string;
}

withDefaults(defineProps<IAccordionProps>(), {
  accordionNo: undefined,
  title: "",
  titleSupp: "",
  body: "",
});
</script>

<style>
.accordion__body {
  display: none;
}

.accordion__radio:checked ~ .accordion__body {
  display: block;
}
</style>

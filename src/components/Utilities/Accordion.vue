<template>
  <section ref="accordionRef" class="accordion" :class="{ active: isOpen }">
    <div class="accordion__label">
      <div class="accordion__title">{{ title }}</div>
      <div class="accordion__title-supp">
        <p>{{ titleSup }}</p>
        <div
          :class="`accordion__circle-plus ${
            isOpen ? 'accordion--opened' : 'accordion--closed'
          }`"
        >
          <div class="accordion__circle">
            <div class="accordion__horizontal-line"></div>
            <div class="accordion__vertical-line"></div>
          </div>
        </div>
      </div>
    </div>

    <section
      class="accordion__body"
      ref="bodyRef"
      :style="{ height: bodyHeight }"
    >
      <div class="accordion__body-content-wrapper">
        <slot name="body"></slot>
      </div>
    </section>
  </section>
</template>

<script setup lang="ts">
import { ref, watch, nextTick } from "vue";

interface IAccordionProps {
  accordionNo: number;
  title: string;
  titleSup?: string;
  body?: string;
  isOpen?: false;
}

const props = withDefaults(defineProps<IAccordionProps>(), {
  accordionNo: undefined,
  title: "",
  titleSupp: "",
  body: "",
  isOpen: false,
});

const isOpen = ref(false);
const bodyRef = ref<HTMLElement | null>();
const accordionRef = ref<HTMLElement | null>();

const bodyHeight = ref("0px");

const toggleAccordion = async (state: boolean) => {
  isOpen.value = state !== undefined ? state : !isOpen.value;

  await nextTick(); // Ensure DOM updates before measuring height

  bodyHeight.value =
    isOpen.value && bodyRef.value ? `${bodyRef.value.scrollHeight}px` : "0px";
};

watch(() => props.isOpen, toggleAccordion);

defineExpose({
  accordionRef,
  toggleAccordion,
});
</script>

<style>
.accordion {
  cursor: pointer;
}

.accordion + .accordion {
  margin-top: 1rem;
}

.accordion__label {
  display: flex;
  align-items: center;
  justify-content: space-between;

  background-color: #740bdc;
  color: #fff;
  border-radius: 0.25rem;
  padding: 0.5rem 1rem;
  height: 4rem;
  align-content: center;
}

.accordion__title-supp {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.accordion__body {
  height: 0;
  overflow: hidden;
  transition: all 0.3s ease-in-out;
}

.accordion__radio {
  display: none;
}

.accordion__body-content-wrapper {
  background-color: #231e41;
  color: #fff;
  padding: 1rem 1.5rem;
}

/* close / open transition */
.closed .accordion__vertical-line {
  transition: all 0.5s ease-in-out;
  transform: rotate(-90deg);
}

.closed .accordion__horizontal-line {
  transition: all 0.5s ease-in-out;
  transform: rotate(-90deg);
  opacity: 1;
}

.accordion--opened {
  opacity: 1;
}

.accordion--opened .accordion__vertical-line {
  transition: all 0.5s ease-in-out;
  transform: rotate(90deg);
}
.accordion--opened .accordion__horizontal-line {
  transition: all 0.5s ease-in-out;
  transform: rotate(90deg);
  opacity: 0;
}

.accordion__circle-plus {
  height: 4em;
  width: 2em;
  font-size: 1em;
}

.accordion__circle-plus .accordion__circle {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.accordion__circle-plus .accordion__circle .accordion__horizontal-line {
  position: absolute;
  background-color: #fff;
  width: 10px;
  height: 2px;
  left: 50%;
  margin-left: -7px;
  top: 61%;
  margin-top: -9.5px;
}
.accordion__circle-plus .accordion__circle .accordion__vertical-line {
  position: absolute;
  background-color: #fff;
  width: 2px;
  height: 10px;
  left: 50%;
  margin-left: -2.5px;
  top: 64%;
  margin-top: -15px;
}

.active .accordion--opened .accordion__circle .accordion__vertical-line {
  background-color: #66d9ed;
}
</style>

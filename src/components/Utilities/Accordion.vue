<template>
  <section ref="accordionRef" class="accordion" :class="{ active: isOpen }">
    <div class="accordion__label">
      <div class="accordion__title">{{ title }}</div>
      <div class="accordion__title-supp">
        <p>{{ titleSup }}</p>
        <div class="accordion__icon-container">
          <Icon
            name="down-caret"
            :class="`accordion__icon ${isOpen ? 'accordion__icon--open' : ''}`"
          />
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
import Icon from "../Icon.vue";

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

.accordion__icon-container {
  min-height: 1.65rem;
  min-width: 1.65rem;
  display: flex;
  align-items: center;
}

.accordion__icon {
  transform: rotate(0deg);
  transition: transform 0.3s ease;
  width: 100%;
  height: 100%;
}

.accordion__icon--open {
  transform: rotate(180deg);
}

@media (max-width: 700px) {
  .accordion__label {
    min-height: 4rem;
    height: auto;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 0.15rem;
  }

  .accordion__title {
    flex: 1 0 100%;
  }

  .accordion__title-supp {
    flex: 1 0 100%;
    justify-content: space-between;
  }
}
</style>

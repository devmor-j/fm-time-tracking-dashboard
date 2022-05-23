<script setup lang="ts">
import BaseCard from "./BaseCard.vue";
import cardStyles from "../assets/card.module.css";
import { computed } from "vue";

const props = defineProps<{
  type: ('work' | 'play' | 'study' | 'exercise' | 'social' | 'self-care'),
}>()

const getTitle = computed(() => {
  const result = props.type[0].toUpperCase() + props.type.slice(1);
  if (props.type === 'self-care') {
    return 'Self Care';
  }
  return result;
})

</script>

<template>
  <div :class="cardStyles['card-wrapper']">
    <!-- top decoration svg icon -->
    <BaseCard class="decoration-wrapper" :style="{ 'background-color': `var(--clr-card-${$props.type})` }">
      <img :src="`src/assets/images/icon-${$props.type}.svg`" alt="" class="decoration" />
    </BaseCard>

    <!-- card main content -->
    <BaseCard>
      <div :class="cardStyles.header">
        <h3 :class="cardStyles.title">{{ getTitle }}</h3>
        <img src="../assets/images/icon-ellipsis.svg" alt="" class="three-dots" />
      </div>

      <div :class="cardStyles.header">
        <h4 :class="cardStyles.duration">32hrs</h4>
        <time datetime="" :class="cardStyles.datetime">Last Week - 36hrs</time>
      </div>
    </BaseCard>
  </div>
</template>

<style scoped>
.decoration-wrapper {
  --padding-inline: 1rem;
  --svg-scale: 0.8;
  width: 100%;
  position: absolute;
  top: -2rem;
  display: flex;
  justify-content: end;
  align-items: center;
  z-index: -1;
  padding: 0 var(--padding-inline);
  overflow: hidden;
}

.decoration {
  margin-block-start: calc(-1 * var(--padding-inline));
  margin-inline-end: calc(-0.5 * var(--padding-inline));
  transform: scale(var(--svg-scale));
  padding-block-end: 2rem;
}
</style>

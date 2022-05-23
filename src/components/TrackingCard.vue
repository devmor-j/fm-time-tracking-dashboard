<script setup lang="ts">
import BaseCard from "./BaseCard.vue";

import cardStyles from "../assets/card.module.css";
</script>

<template>
  <div :class="cardStyles['card-wrapper']">
    <!-- top decoration svg icon -->
    <BaseCard class="decoration-wrapper">
      <img src="../assets/images/icon-work.svg" alt="" class="decoration" />
    </BaseCard>

    <!-- card main content -->
    <BaseCard>
      <div :class="cardStyles.header">
        <h3 :class="cardStyles.title">Work</h3>
        <img src="../assets/images/icon-ellipsis.svg" alt="" />
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
  background-color: var(--clr-light-red-1);
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
}
</style>

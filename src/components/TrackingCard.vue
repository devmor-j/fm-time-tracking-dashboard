<script setup lang="ts">
import BaseCard from "./BaseCard.vue";
import IconEllipsis from "./icons/IconEllipsis.vue";

import cardStyles from "../assets/card.module.css";
</script>

<template>
  <BaseCard>
    <div :class="cardStyles.header">
      <h3 :class="cardStyles.title">Work</h3>
      <IconEllipsis />
    </div>
    <div :class="cardStyles.header">
      <h4 :class="cardStyles.duration">32hrs</h4>
      <time datetime="" :class="cardStyles.datetime">Last Week - 36hrs</time>
    </div>
  </BaseCard>
</template>

<style scoped>
</style>

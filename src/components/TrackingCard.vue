<script setup lang="ts">
import BaseCard from "./BaseCard.vue";
import IconEllipsis from "./icons/IconEllipsis.vue";

import cardStyles from "../assets/card.module.css";
</script>

<template>
  <BaseCard>
    <div>
      <h3>Work</h3>
      <IconEllipsis />
    </div>
    <div>
      <h4>32hrs</h4>
      <time datetime="">Last Week - 36hrs</time>
    </div>
  </BaseCard>
</template>

<style scoped>
</style>

<script setup lang="ts">
import cardStyles from "@/assets/scss/card.module.scss";
</script>

<template>
  <div class="card" :class="cardStyles['base-dark-blue']">
    <slot></slot>
  </div>
</template>

<style lang="scss">
.card {
  border-radius: 1rem;
  padding: 1.25rem;
}
</style>

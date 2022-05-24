<script setup lang="ts"></script>

<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style lang="scss">
@use "../assets/scss/breakpoints" as bp;
@use "../assets/scss/colors" as clr;

.card {
  background-color: clr.$dark-blue;
  border-radius: 1rem;
  padding: 1.25rem;
}

@media (min-width: bp.$tablet) {
  .card {
    padding-inline: 1.5rem;
  }
}
</style>

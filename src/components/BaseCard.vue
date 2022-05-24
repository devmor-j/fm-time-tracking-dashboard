<script setup lang="ts"></script>

<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style lang="scss">
.card {
  background-color: var(--clr-dark-blue);
  border-radius: 1rem;
  padding: 1.25rem;
}
</style>

<script setup lang="ts"></script>

<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style>
.card {
  background-color: var(--clr-dark-blue);
  width: min(calc(100% - 2 * 1rem), 18rem);
  border-radius: 1rem;
  padding: 1.25rem;
}
</style>

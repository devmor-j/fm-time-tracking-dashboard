<script setup lang="ts">
import TrackingCard from "./components/TrackingCard.vue";
import ProfileCard from "./components/ProfileCard.vue";
</script>

<template>
  <main class="container">
    <ProfileCard />
    <TrackingCard />
  </main>
</template>

<style>
@import "./assets/base.css";

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-block: 4rem;
}
</style>

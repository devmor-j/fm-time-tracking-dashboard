<script setup lang="ts">
import TrackingCard from "./components/TrackingCard.vue";
import ProfileCard from "./components/ProfileCard.vue";
</script>

<template>
  <main class="container">
    <ProfileCard />
    <TrackingCard class="first-tracking-card" />
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
  gap: 1.5rem;
  --card-overlap-size: 1.5rem;
  --profile-card-transform: calc(-1.25 * var(--card-overlap-size));
}

.first-tracking-card {
  margin: 0;
}
</style>

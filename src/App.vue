<script setup lang="ts">
import TrackingCard from "./components/TrackingCard.vue";
import ProfileCard from "./components/ProfileCard.vue";
</script>

<template>
  <main class="container">
    <ProfileCard class="profile-card" />
    <TrackingCard type="work" />
    <TrackingCard type="play" />
    <TrackingCard type="study" />
    <TrackingCard type="exercise" />
    <TrackingCard type="social" />
    <TrackingCard type="self-care" />
  </main>
</template>

<style lang="scss">
@use "./assets/breakpoints"as break;
@import "./assets/base.css";

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: min(100%, 60rem);

  padding-block: 4rem;
  row-gap: 1.5rem;
  --card-overlap-size: 1.5rem;
  --profile-card-transform: calc(-1.25 * var(--card-overlap-size));
}

.profile-card {
  margin: 0;
}

@media screen and (min-width: break.$tablet) {
  .profile-card {
    grid-row: 1/3;
  }

  .container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    align-items: initial;
    row-gap: 0rem;
    place-items: center;
  }
}
</style>

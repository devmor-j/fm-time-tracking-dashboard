<script setup lang="ts">
import { ref } from "vue";
import TrackingCard from "./components/TrackingCard.vue";
import ProfileCard from "./components/ProfileCard.vue";
import type { Timeframe } from "./types/Timeframe";

import trackingData from "./assets/data.json";
import type { TrackingType } from "./types/TrackingType";

const timeframe = ref<Timeframe>("weekly");

function onTimeframeChanged(selectedTimeframe: Timeframe) {
  // update TrackingCard's data based on new timeframe selected on ProfileCard
  timeframe.value = selectedTimeframe;
}

function fixTitles(title: string): TrackingType {
  return title.toLowerCase().replace(/\s/g, '-') as TrackingType;
}
</script>

<template>
  <main class="container">
    <ProfileCard class="profile-card" @timeframe-changed="onTimeframeChanged" />
    <TrackingCard v-for="(data, index) in trackingData" :key="index" :tracking-type="fixTitles(data.title)" :tracking-stats="data.timeframes" :tracking-timeframe="timeframe" />
  </main>
</template>

<style lang="scss">
@use "./assets/scss/base";
@use "./assets/scss/breakpoints"as bp;

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

@media screen and (min-width: bp.$tablet) {
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

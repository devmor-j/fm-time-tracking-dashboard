<script setup lang="ts">
import { ref } from "vue";
import TrackingCard from "./components/TrackingCard.vue";
import ProfileCard from "./components/ProfileCard.vue";
import type { ProfileTimeframe } from "@/types/ProfileTimeframe";
import type { TrackingData } from "@/types/TrackingData";

import rawData from "./assets/raw_data.json";

// declare type on raw data as an array of TrackingData type
const trackingData: Array<TrackingData> = rawData;
const profileTimeframe = ref<ProfileTimeframe>("weekly");

function onProfileTimeframeChange(selectedTimeframe: ProfileTimeframe) {
  // update TrackingCard's data based on new timeframe selected on ProfileCard
  profileTimeframe.value = selectedTimeframe;
}
</script>

<template>
  <main class="container">
    <ProfileCard
      class="profile-card"
      @timeframe-change="onProfileTimeframeChange"
    />
    <TrackingCard
      v-for="(data, index) in trackingData"
      :key="index"
      :tracking-data="data"
      :tracking-timeframe="profileTimeframe"
    />
  </main>
</template>

<style lang="scss">
@use "./assets/scss/base";
@use "./assets/scss/breakpoints" as bp;

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

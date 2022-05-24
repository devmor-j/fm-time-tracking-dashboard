<script setup lang="ts">
import { ref } from "vue";
import TrackingCard from "./components/TrackingCard.vue";
import ProfileCard from "./components/ProfileCard.vue";
import type { Timeframe } from "./types/Timeframe";

import trackingData from "./assets/data.json";

const timeframe = ref<Timeframe>("weekly");

function onTimeframeChanged(selectedTimeframe: Timeframe) {
  // update TrackingCard's data based on new timeframe selected on ProfileCard
  timeframe.value = selectedTimeframe;
}
</script>

<template>
  <main class="container">
    <ProfileCard class="profile-card" @timeframe-changed="onTimeframeChanged" />
    <TrackingCard
      tracking-type="work"
      :tracking-stats="trackingData[0].timeframes"
      :tracking-timeframe="timeframe"
    />
    <TrackingCard
      tracking-type="play"
      :tracking-stats="trackingData[1].timeframes"
      :tracking-timeframe="timeframe"
    />
    <TrackingCard
      tracking-type="study"
      :tracking-stats="trackingData[2].timeframes"
      :tracking-timeframe="timeframe"
    />
    <TrackingCard
      tracking-type="exercise"
      :tracking-stats="trackingData[3].timeframes"
      :tracking-timeframe="timeframe"
    />
    <TrackingCard
      tracking-type="social"
      :tracking-stats="trackingData[4].timeframes"
      :tracking-timeframe="timeframe"
    />
    <TrackingCard
      tracking-type="self-care"
      :tracking-stats="trackingData[5].timeframes"
      :tracking-timeframe="timeframe"
    />
  </main>
</template>

<style lang="scss">
@use "./assets/breakpoints" as break;
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

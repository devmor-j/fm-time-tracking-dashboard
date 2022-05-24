<script setup lang="ts">
import { ref, watch } from "vue";
import BaseCard from "./BaseCard.vue";
import cardStyles from "../assets/card.module.scss";
import type { Timeframe } from "../types/Timeframe";

const emits = defineEmits(["timeframeChanged"]);

const selectedTimeframe = ref<Timeframe>("weekly");

watch(selectedTimeframe, () => {
  emits("timeframeChanged", selectedTimeframe.value);
});
</script>

<template>
  <div :class="cardStyles['card-wrapper']">
    <!-- profile content -->
    <BaseCard class="profile-wrapper">
      <!-- width=64 is set inline to prevent layout shift -->
      <!-- image class can be used to override width -->
      <img
        src="../assets/images/image-jeremy.png"
        alt="Jeremy profile image"
        class="profile-image"
        width="56"
      />
      <div>
        <span class="report-for">Report for</span>
        <h3 class="profile-name">Jeremy Robson</h3>
      </div>
    </BaseCard>
    <!-- interval selection -->
    <BaseCard class="interval-wrapper">
      <ul class="interval" role="list">
        <li
          @click="selectedTimeframe = 'daily'"
          :class="{ active: selectedTimeframe == 'daily' }"
        >
          Daily
        </li>
        <li
          @click="selectedTimeframe = 'weekly'"
          :class="{ active: selectedTimeframe == 'weekly' }"
        >
          Weekly
        </li>
        <li
          @click="selectedTimeframe = 'monthly'"
          :class="{ active: selectedTimeframe == 'monthly' }"
        >
          Monthly
        </li>
      </ul>
    </BaseCard>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/breakpoints" as break;

.profile-wrapper {
  display: flex;
  align-items: center;
  gap: 1rem;
  background-color: var(--clr-blue);
  font-weight: 300;
  padding: 1.5rem;
  z-index: 1;
  position: relative;
}

.profile-image {
  width: 3.5rem;
  border: 2.5px solid whitesmoke;
  border-radius: 50%;
}

.report-for {
  color: var(--clr-pale-blue);
  font-size: 0.75rem;
}

.profile-name {
  font-weight: inherit;
}

.interval-wrapper {
  transform: translateY(var(--profile-card-transform));
}

.interval {
  display: flex;
  justify-content: space-between;
  list-style: none;
  color: var(--clr-desaturated-blue);
  padding-inline: 0rem;
  margin-block-start: var(--card-overlap-size);
  margin-block-end: 0rem;
  font-size: 0.875rem;
}

.interval > li {
  cursor: pointer;
}

.interval .active {
  color: whitesmoke;
}

@media screen and (min-width: break.$tablet) {
  .profile-wrapper {
    flex-direction: column;
  }

  .profile-image {
    align-self: start;
    width: 4rem;
    margin-block-end: 00.5rem;
  }

  .profile-name {
    font-size: 2rem;
    line-height: 1.25;
    padding-block-end: 2rem;
  }

  .interval {
    flex-direction: column;
  }

  .interval > li {
    padding-block: 0.5rem;
  }
}
</style>

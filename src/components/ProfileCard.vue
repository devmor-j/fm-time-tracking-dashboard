<script setup lang="ts">
import { ref, watch } from "vue";
import BaseCard from "./BaseCard.vue";
import cardStyles from "@/assets/scss/card.module.scss";
import type { ProfileTimeframe } from "@/types/ProfileTimeframe";

const emits = defineEmits(["timeframeChange"]);

const selectedTimeframe = ref<ProfileTimeframe>("weekly");

watch(selectedTimeframe, () => {
  emits("timeframeChange", selectedTimeframe.value);
});
</script>

<template>
  <div :class="cardStyles['card-wrapper']">
    <!-- profile content -->
    <BaseCard class="profile-wrapper" :class="cardStyles['profile-blue']">
      <!-- width=64 is set inline to prevent layout shift -->
      <!-- image class can be used to override width -->
      <img
        src="../assets/images/image-jeremy.png"
        alt="Jeremy profile image"
        class="profile-image"
        width="56"
      />
      <div>
        <span class="report-for" :class="cardStyles['clr-pale-blue']"
          >Report for</span
        >
        <h3 class="profile-name">Jeremy Robson</h3>
      </div>
    </BaseCard>
    <!-- profile timeframe selection -->
    <BaseCard class="timeframe-wrapper">
      <ul
        class="timeframe"
        :class="cardStyles['profile-desaturated-blue']"
        role="list"
      >
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
@use "../assets/scss/breakpoints" as bp;

.profile-wrapper {
  display: flex;
  align-items: center;
  gap: 1rem;
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
  font-size: 0.75rem;
}

.profile-name {
  font-weight: inherit;
}

.timeframe-wrapper {
  transform: translateY(var(--profile-card-transform));
}

.timeframe {
  display: flex;
  justify-content: space-between;
  list-style: none;
  padding-inline: 0rem;
  margin-block-start: var(--card-overlap-size);
  margin-block-end: 0rem;
  font-size: 0.875rem;
}

.timeframe > li {
  cursor: pointer;
  transition: color 0.15s linear;

  &:hover {
    color: hsl(236, 100%, 87%);
  }
}

.timeframe .active {
  color: whitesmoke;
}

@media screen and (min-width: bp.$tablet) {
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

  .timeframe {
    flex-direction: column;
  }

  .timeframe > li {
    padding-block: 0.5rem;
  }
}
</style>

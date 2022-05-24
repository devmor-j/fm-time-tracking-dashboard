<script setup lang="ts">
import { computed } from "vue";
import BaseCard from "./BaseCard.vue";
import IconEllipsis from "./icons/IconEllipsis.vue";
import cardStyles from "@/assets/scss/card.module.scss";
import type { TrackingData } from "@/types/TrackingData";
import type { ProfileTimeframe } from "@/types/ProfileTimeframe";

const props = defineProps<{
  trackingData: TrackingData;
  trackingTimeframe: ProfileTimeframe;
}>();

// note that we can't use a ref on props.trackingData directly
// because DOM is not ready to be called on template
const tracking = computed(() => {
  return props.trackingData;
});

const timeframeToTime = computed(() => {
  // example 'daily' => 'Day'
  let result;
  switch (props.trackingTimeframe) {
    case "daily":
      result = "Day";
      break;
    case "weekly":
      result = "Week";
      break;
    case "monthly":
      result = "Month";
      break;

    // just in case we put default value
    default:
      result = "Time";
      break;
  }

  return result;
});

function toLowerCaseNoSpace(title: string): string {
  return title.toLowerCase().replace(/\s/g, "-");
}
</script>

<template>
  <div :class="cardStyles['card-wrapper']">
    <!-- top decoration svg icon -->
    <BaseCard
      class="decoration-wrapper"
      :style="{
        'background-color': `var(--clr-card-${toLowerCaseNoSpace(
          $props.trackingData.title
        )})`,
      }"
    >
      <img
        :src="`src/assets/images/icon-${toLowerCaseNoSpace(
          $props.trackingData.title
        )}.svg`"
        alt=""
        class="decoration"
      />
    </BaseCard>

    <!-- card main content -->
    <BaseCard class="card-content">
      <div :class="cardStyles.header">
        <h3 :class="cardStyles.title">{{ $props.trackingData.title }}</h3>
        <IconEllipsis />
      </div>
      <div :class="[cardStyles.header, cardStyles['column-header']]">
        <h4 :class="cardStyles.duration">
          {{ tracking.timeframes[trackingTimeframe].current }}hrs
        </h4>
        <time datetime="" :class="cardStyles.datetime"
          >Last {{ timeframeToTime }} -
          {{ tracking.timeframes[trackingTimeframe].previous }}hrs</time
        >
      </div>
    </BaseCard>
  </div>
</template>

<style lang="scss" scoped>
$padding-inline: 1rem;
$svg-scale: 0.8;
.decoration-wrapper {
  width: 100%;
  position: absolute;
  top: -2rem;
  display: flex;
  justify-content: end;
  align-items: center;
  z-index: -1;
  padding: 0 $padding-inline;
  overflow: hidden;
}

.decoration {
  margin-block-start: calc(-1 * $padding-inline);
  margin-inline-end: calc(-0.5 * $padding-inline);
  transform: scale($svg-scale);
  padding-block-end: 2rem;
}

.card-content {
  transition: background-color 0.15s linear;

  &:hover {
    background-color: lighten($color: hsl(235, 46%, 15%), $amount: 15%);
  }
}
</style>

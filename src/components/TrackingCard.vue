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

function toLowerCaseAndSpaceToHyphen(title: string): string {
  // example 'Some Text' => 'some-text'
  return title.toLowerCase().replace(/\s/g, "-");
}

// example '4hrs' or '1hr' or 'zero'
const getTracking = computed(() => {
  let { current: cur, previous: pre } =
    tracking.value.timeframes[props.trackingTimeframe];
  const result: { current: string; previous: string } = {
    current: cur.toString(),
    previous: pre.toString(),
  };

  if (cur > 1) {
    result.current = cur + "hrs";
  }
  if (pre > 1) {
    result.previous = pre + "hrs";
  }

  if (cur === 1) {
    result.current = cur + "hr";
  }
  if (pre === 1) {
    result.previous = pre + "hr";
  }

  if (cur < 1) {
    result.current = "zero";
  }
  if (pre < 1) {
    result.previous = "zero";
  }

  return result;
});

const getSvgPath = computed(() => {
  // example for title='work' => '/images/icon-work.svg'
  const svgName = toLowerCaseAndSpaceToHyphen(props.trackingData.title);
  const svgPath = `/images/icon-${svgName}.svg`;
  console.log(svgPath);
  return svgPath;
});
</script>

<template>
  <div :class="cardStyles['card-wrapper']">
    <!-- top decoration svg icon -->
    <BaseCard
      class="decoration-wrapper"
      :class="
        cardStyles[
          `tracking-${toLowerCaseAndSpaceToHyphen(props.trackingData.title)}`
        ]
      "
    >
      <img :src="getSvgPath" alt="" class="decoration" />
    </BaseCard>

    <!-- card main content -->
    <BaseCard class="card-content">
      <div :class="cardStyles.header">
        <h3 :class="cardStyles.title">{{ $props.trackingData.title }}</h3>
        <IconEllipsis />
      </div>
      <div :class="[cardStyles.header, cardStyles['column-header']]">
        <h4 :class="cardStyles.duration">
          {{ getTracking.current }}
        </h4>
        <time
          :datetime="`PT${
            tracking.timeframes[props.trackingTimeframe].previous
          }H`"
          :class="cardStyles['datetime']"
          >Last {{ timeframeToTime }} - {{ getTracking.previous }}</time
        >
      </div>
    </BaseCard>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/scss/colors" as clr;

$svg-padding: 1rem;
$svg-scale: 0.8;

.decoration-wrapper {
  width: 100%;
  position: absolute;
  top: -2rem;
  display: flex;
  justify-content: end;
  align-items: center;
  z-index: -1;
  padding: 0 $svg-padding;
  overflow: hidden;
}

.decoration {
  margin-block-start: calc(-1 * $svg-padding);
  margin-inline-end: calc(-0.5 * $svg-padding);
  transform: scale($svg-scale);
  padding-block-end: 2rem;
}

.card-content {
  transition: background-color 0.15s linear;

  &:hover {
    background-color: lighten($color: clr.$dark-blue, $amount: 10%);
  }
}
</style>

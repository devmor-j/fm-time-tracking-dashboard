<script setup lang="ts">
import BaseCard from "./BaseCard.vue";

import cardStyles from "../assets/card.module.css";
</script>

<template>
  <div :class="cardStyles['card-wrapper']">

    <!-- profile content -->
    <BaseCard class="profile-wrapper">
      <!-- width=64 is set inline to prevent layout shift -->
      <!-- image class can be used to override width -->
      <img src="../assets/images/image-jeremy.png" alt="Jeremy profile image" class="profile-image" width="56">

      <div>
        <span class="report-for">Report for</span>
        <h3 class="profile-name">Jeremy Robson</h3>
      </div>
    </BaseCard>

    <!-- interval selection -->
    <BaseCard class="interval-wrapper">
      <ul class="interval" role="list">
        <li>Daily</li>
        <li class="active">Weekly</li>
        <li>Monthly</li>
      </ul>
    </BaseCard>

  </div>
</template>

<style scoped>
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
</style>

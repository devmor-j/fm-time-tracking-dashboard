<template>
  <svg
    class="three-dots"
    width="37"
    height="21"
    xmlns="http://www.w3.org/2000/svg"
  >
    <path
      d="M2.5 0a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5Zm8 0a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5Zm8 0a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5Z"
      fill="#BBC0FF"
      fill-rule="evenodd"
    />
  </svg>
</template>

<style lang="scss" scoped>
@use "@/assets/scss/colors" as clr;
.three-dots {
  cursor: pointer;
  padding: 8px;
  border-radius: 1rem;
  transition: background-color 0.15s ease-in-out;
}

.three-dots:hover {
  background-color: clr.$low-opacity-white;
}

.three-dots > path {
  transition: fill 0.1s linear;
}

.three-dots:hover > path {
  fill: whitesmoke;
}
</style>

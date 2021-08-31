<template>
  <div class="controls">
    <div class="controls__toggle">Toggles</div>
    <div class="controls__sort">Sort</div>
  </div>
</template>

<style lang="scss" scoped>
@import "@/styles/_app.scss";

.controls {
  text-align: center;

  &__toggle,
  &__sort {
    padding: 1rem;
  }

  &__toggle {
    padding-bottom: 0;
  }
}

@include media-breakpoint-up(md) {
  .controls {
    display: flex;
    justify-content: space-evenly;
    margin-bottom: 1rem;
  }
}
</style>

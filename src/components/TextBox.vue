<template>
  <div class="box">
    <slot></slot>
  </div>
</template>

<style lang="scss" scoped>
@import "@/styles/_app.scss";
.box {
  border: 2px solid rgba($text-light, 0.4);
  border-radius: 15px;
  background-color: $accent-light;
  padding: 1rem;
}
</style>

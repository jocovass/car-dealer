<template>
  <b-button class="button">
    <slot></slot>
    {{ text }}
  </b-button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/_app.scss";

.button {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 10px;
  background-color: $accent;
  font-family: $headings-font-family;
  line-height: normal;
  padding: 0.6em 1.1em;

  &:hover,
  &:focus,
  &:active {
    background-color: darken($accent, 5%) !important;
  }
}
</style>

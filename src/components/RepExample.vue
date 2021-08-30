<template>
  <div class="rep-outer">
    <div class="d-flex flex-column">
      <p class="rep-example-text">
        <b>Representative example: </b>Borrowing $11,790.00 over 4 years with a
        representative APR of 7.9%, an annual interest rate of 4.08% (Fixed) and
        a deposit of $500.00, the amount payable would be $273.59 per month,
        with a total cost of credit of $1,843.32 and a total amount payable of
        $13,633.32.
      </p>
      <b-button @click="toggleSpecs" class="toggle">
        Show Breakdown <span>&or;</span>
      </b-button>
    </div>
    <RepSpecs v-show="isOpen" />
  </div>
</template>

<script>
import RepSpecs from "./RepSpecs.vue";

export default {
  name: "RepExample",
  components: { RepSpecs },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    toggleSpecs() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/_app.scss";
.rep-example-text {
  font-weight: 300;
  font-size: 0.875rem;
}
.toggle {
  background-color: $background !important;
  color: $text-lighter !important;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.7rem 1rem;
  border-color: $background !important;
  border-radius: 10px;
  color: $text-lighter;

  span {
    background-color: $text-light;
    color: $background;
    line-height: normal;
    padding: 0.2em 0.5em;
    border-radius: 10px;
  }
}
</style>

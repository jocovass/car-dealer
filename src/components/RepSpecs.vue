<template>
  <div class="repspecs__outer">
    <div class="repspecs__toggles">
      <b-button title="Personal Contract Purchase" class="active">
        PCP
      </b-button>
      <b-button title="Hire Purchase"> HP </b-button>
    </div>
    <div class="repspecs__list">
      <div class="repspecs__item" v-for="spec in specs" :key="spec.label">
        <p class="repspecs__label">{{ spec.label }}</p>
        <p class="repspecs__value">{{ spec.spec }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RepSpecs",
  data() {
    return {
      specs: [
        { label: "48 monthly payments", spec: "$157.25" },
        { label: "Cash price", spec: "$9,998.00" },
        { label: "Customer deposit", spec: "$250.00" },
        { label: "Amount of credit", spec: "$11,980.75" },
        { label: "APR", spec: "$7.9%" },
        { label: "Term", spec: "$48 months" },
        { label: "Total amount payable", spec: "$12.163.72" },
        { label: "Rate of interest (fixed)", spec: "$4.08% PA" },
        { label: "Annual mileage", spec: "$8,000" },
        { label: "Optional final payment", spec: "$3,888.04" },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/_app.scss";
.repspecs {
  &__toggles {
    display: flex;
    margin-bottom: 1.2rem;

    button {
      font-size: 0.75rem;
      background-color: transparent;
      border: 2px solid transparent;
      border-radius: 0;
      border-bottom-color: rgba($text-light, 0.5);
      color: $text-dark;
      width: 100%;

      &.active {
        border-color: transparent !important;
        border-bottom-color: $accent !important;
        background-color: transparent !important;
        color: $text-dark !important;
      }

      &:hover {
        background-color: rgba($text-light, 0.2) !important;
      }
    }
  }

  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  &__item {
    background-color: $background;
    padding: 0.8rem 0.1rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
    width: 48%;
    text-align: center;
    margin-bottom: 1rem;
  }

  &__label {
    font-size: 0.78rem;
    color: $text-lighter;
    font-weight: 300;
    margin-bottom: 3px;
  }

  &__value {
    font-weight: 500;
    margin-bottom: 0;
    font-size: 0.9rem;
  }
}
</style>

<template>
  <div class="home">
    <b-container>
      <MobileCarCard v-for="car in cars" :key="car.stock_id" :car="car" />
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import MobileCarCard from "../components/MobileCarCard.vue";
import json from "../data/vehicle-search.json";

export default {
  name: "ProductListing",
  components: {
    MobileCarCard,
  },
  data() {
    return {
      currentPage: 2,
      itemPerPage: 6,
      cars: [],
    };
  },
  created() {
    const start = (this.currentPage - 1) * 6;
    this.cars = json.data.slice(start, start + this.itemPerPage);
  },
};
</script>
<!--
  body_type, colour, feature_classification[0], make, model, odometer_value, original_price, price, model_year, monthly_payment, stock_id, transmission, year, advert_classification

  year, make model   advert_classification, star
  name

  odometer_value transmission fuel_type body_type    monthly_payment
                                                      original_price price
 -->

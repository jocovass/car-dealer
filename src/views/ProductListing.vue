<template>
  <div class="productlist">
    <b-container>
      <div class="d-block d-md-flex flex-wrap justify-content-between">
        <MobileCarCard v-for="car in cars" :key="car.stock_id" :car="car" />
      </div>
      <Button text="Filter">
        <b-icon
          icon="filter"
          aria-hidden="true"
          style="margin-right: 3px"
        ></b-icon>
      </Button>
      <Pagination />
      <TextBox>
        <RepExample />
      </TextBox>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import MobileCarCard from "../components/MobileCarCard.vue";
import Button from "@/components/Button.vue";
import Pagination from "@/components/Pagination.vue";
import TextBox from "@/components/TextBox.vue";
import RepExample from "@/components/RepExample.vue";
import json from "../data/vehicle-search.json";

export default {
  name: "ProductListing",
  components: {
    MobileCarCard,
    Button,
    Pagination,
    TextBox,
    RepExample,
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

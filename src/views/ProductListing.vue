<template>
  <div class="product-list-view">
    <FinanceBanner />
    <b-container style="max-width: 1440px" class="container">
      <SideBar />
      <div>
        <Controls />
        <div class="d-block d-md-flex flex-wrap justify-content-center">
          <CarCard v-for="car in cars" :key="car.stock_id" :car="car" />
        </div>
        <Pagination />
        <TextBox style="width: 95%; margin: 0 auto">
          <RepExample />
        </TextBox>
        <div class="filter-btn-wrap">
          <Button text="Filter">
            <b-icon
              icon="filter"
              aria-hidden="true"
              style="margin-right: 3px"
            ></b-icon>
          </Button>
        </div>
      </div>
    </b-container>
  </div>
</template>

<script>
import FinanceBanner from "@/components/FinanceBanner.vue";
import Controls from "@/components/Controls.vue";
import SideBar from "@/components/SideBar.vue";
import CarCard from "../components/CarCard.vue";
import Button from "@/components/Button.vue";
import Pagination from "@/components/Pagination.vue";
import TextBox from "@/components/TextBox.vue";
import RepExample from "@/components/RepExample.vue";
import json from "../data/vehicle-search.json";

export default {
  name: "ProductListing",
  components: {
    FinanceBanner,
    Controls,
    SideBar,
    CarCard,
    Button,
    Pagination,
    TextBox,
    RepExample,
  },
  data() {
    return {
      currentPage: 2,
      itemPerPage: 6,
      cars: json.data,
    };
  },
};
</script>

<style lang="scss" scoped>
.filter-btn-wrap {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
}
@media only screen and (min-width: 1400px) {
  .container {
    display: flex;
  }

  .filter-btn-wrap {
    display: none;
  }
}
</style>

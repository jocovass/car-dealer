<template>
  <div class="home">
    <b-container>
      <MobileCarCard />
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import MobileCarCard from "../components/MobileCarCard.vue";

export default {
  name: "ProductListing",
  components: {
    MobileCarCard,
  },
};
</script>

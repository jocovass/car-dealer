<template>
  <div id="app">
    <Header />
    <main class="mb-5">
      <Controls />
      <router-view />
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Controls from "./components/Controls.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: { Header, Controls, Footer },
};
</script>

<style lang="scss">
@import "./styles/_app.scss";

body {
  color: $text-dark !important;
}
</style>

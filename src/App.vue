<template>
  <div id="app">
    <Header />
    <main>
      <Controls />
      <router-view />
    </main>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Controls from "./components/Controls.vue";

export default {
  name: "App",
  components: { Header, Controls },
};
</script>

<style lang="scss">
@import "./styles/_app.scss";

body {
  color: $text-dark !important;
}
</style>

<template>
  <footer class="footer">
    <p class="logo">CarDealer<sup>UK</sup></p>
  </footer>
</template>

<style lang="scss">
@import "../styles/app.scss";

.footer {
  padding: 3rem 0.8rem 0.8rem;
  border-bottom: 1px solid $text-light;
  background-color: $dark;
  height: 200px;
  border-top-right-radius: 35px;
  text-align: center;

  .logo {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 0;
    color: $background;

    sup {
      font-size: 0.9rem;
      color: $accent;
    }
  }
}
</style>

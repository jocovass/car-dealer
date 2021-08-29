<template>
  <header class="header">
    <h1 class="logo">CarDealer<sup>UK</sup></h1>
  </header>
</template>

<style lang="scss">
@import "../styles/app.scss";

.header {
  padding: 1.1rem 0.8rem 0.8rem;
  border-bottom: 1px solid $text-light;

  .logo {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 0;

    sup {
      font-size: 0.9rem;
      color: $accent;
    }
  }
}
</style>

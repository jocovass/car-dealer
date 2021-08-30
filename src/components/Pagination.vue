<template>
  <section class="pagination-wrap">
    <div class="pagination">
      <b-button>&lt;</b-button>
      <b-button class="active">1</b-button>
      <b-button>2</b-button>
      <b-button>&gt;</b-button>
    </div>
    <div class="scroll-totop">
      <a href="#top">Back to top</a>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../styles/_app.scss";

.pagination-wrap {
  margin-bottom: 3rem;
}
.pagination {
  display: flex;
  justify-content: center;
  margin-bottom: 1.5rem;

  button {
    margin-right: 5px;
    background-color: transparent;
    color: $text-lighter;
    border-color: rgba($text-light, 0.4);
    padding: 0.1rem 1.3rem;
    border-radius: 7px;

    &:hover,
    &:active,
    &:focus,
    &.active {
      border-color: $accent !important;
      background-color: $accent !important;
      color: $background !important;
    }
  }
}

.scroll-totop {
  text-align: center;
  a {
    color: $text-lighter;
    text-decoration: underline;
  }
}
</style>

<template>
  <section class="pagination-wrap d-md-flex align-items-md-center">
    <div class="pagination order-2 align-self-center">
      <b-button>&lt;</b-button>
      <b-button class="active">1</b-button>
      <b-button>2</b-button>
      <b-button>&gt;</b-button>
    </div>
    <div class="scroll-totop order-1 mr-auto">
      <a href="#top">Back to top</a>
    </div>
    <div class="sort-container order-3 d-none d-md-block ml-auto">
      <select name="sort" id="sort" class="sort">
        <option value="Lowest Price">Lowest Price</option>
      </select>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../styles/_app.scss";

.pagination-wrap {
  margin-bottom: 2rem;
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

.sort {
  background-color: rgba($text-light, 0.2);
  border: none;
  color: $text-lighter;
  font-weight: 300;
  font-size: 0.9rem;
  padding: 0.6rem 0.3rem;
  border-radius: 8px;
}

@include media-breakpoint-up(md) {
  .pagination {
    margin-bottom: 0;
  }
}
</style>

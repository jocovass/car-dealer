<template>
  <div class="card" style="border: none">
    <div class="card__img-slide">
      <carousel :perPage="3" :paginationEnabled="false">
        <slide class="slide">
          <img src="../assets/images/mercedes.jpg" alt="Mercedes" />
        </slide>
        <slide class="slide">
          <img src="../assets/images/mercedes.jpg" alt="Mercedes" />
        </slide>
        <slide class="slide">
          <img src="../assets/images/mercedes.jpg" alt="Mercedes" />
        </slide>
        <slide class="slide">
          <img src="../assets/images/mercedes.jpg" alt="Mercedes" />
        </slide>
        <slide class="slide">
          <img src="../assets/images/mercedes.jpg" alt="Mercedes" />
        </slide>
      </carousel>
    </div>
    <div class="card__details">
      <header class="card__header">
        <b-row class="align-items-start">
          <b-col class="col-8">
            <div class="card__heading">
              <h3 class="card__title">2014 (64) Mercedes-Benz</h3>
              <p class="card__subtitle">CLA 250e Coupe Shooting Break</p>
            </div>
          </b-col>
          <b-col class="d-flex align-items-center">
            <div class="card__tags">
              <b-badge class="font-weight-normal condition-badge mr-3"
                >New</b-badge
              >
              <b-icon icon="star" aria-hidden="true" :font-scale="1.3"></b-icon>
            </div>
          </b-col>
        </b-row>
      </header>

      <div class="card__body">
        <b-row>
          <b-col>
            <div class="card__specs">
              <span class="card__spec">32 miles</span>
              <span class="card__spec--divider"> | </span>
              <span class="card__spec">Hybrid</span>
              <span class="card__spec--divider"> | </span>
              <span class="card__spec">Manual</span>
              <span class="card__spec--divider"> | </span>
              <span class="card__spec">SUV</span>
            </div>
          </b-col>
          <b-col>
            <div class="card__pricing">
              <div class="card__pricing--monthly">
                <p><span>$550.90</span> /mo (PCP)</p>
              </div>
              <div class="card__pricing--full d-flex">
                <p class="card__pricing--new mr-2">$23,300</p>
                <p class="card__pricing--old">$23,300</p>
              </div>
            </div>
          </b-col>
        </b-row>
      </div>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from "vue-carousel";

export default {
  name: "MobileCarCard",
  components: { Carousel, Slide },
};
</script>

<style lang="scss" scoped>
@import "../styles/app.scss";

.slide {
  margin-bottom: 1.5rem;
  padding-right: 0.5rem;

  img {
    width: 100%;
    height: auto;
    border-radius: 10px;
  }
}

.card {
  &__title {
    font-size: 0.9rem;
    font-family: $font-family-base;
    font-weight: 400;
    margin-bottom: 0.2rem;
  }

  &__subtitle {
    font-size: 0.8rem;
    color: $text-lighter;
  }

  .condition-badge {
    background-color: $dark-light;
    padding: 0.5em 0.8em;
    border-radius: 8px;
  }

  &__spec,
  &__spec--divider {
    font-size: 0.8rem;
    color: $text-lighter;
    display: inline-block;
  }

  &__spec--divider {
    color: rgba($text-light, 0.5);
    margin: 0 6px;
  }

  &__pricing {
    font-size: 0.8rem;

    p {
      margin-bottom: 0;
    }

    &--monthly {
      p {
        margin-bottom: 3px;
      }
      span {
        font-size: 0.9rem;
        font-weight: 700;
      }
    }

    &--new {
      color: $accent2;
    }

    &--old {
      color: $text-lighter;
      text-decoration: line-through;
    }
  }
}
</style>

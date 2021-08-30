<template>
  <div class="card" style="border: none">
    <div class="card__img-slide">
      <carousel :perPage="3" :paginationEnabled="false">
        <slide class="slide" v-for="index in 5" :key="index">
          <img :src="getImages" alt="Mercedes" />
        </slide>
        <!-- <slide class="slide">
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
        </slide> -->
      </carousel>
    </div>
    <div class="card__details">
      <header class="card__header">
        <b-row class="align-items-start">
          <b-col class="col-8">
            <div class="card__heading">
              <h3 class="card__title">
                {{ car.year ? car.year : null }}
                {{ car.make ? car.make : null }}
                {{ car.model ? car.model : null }}
              </h3>
              <p class="card__subtitle">{{ car.name }}</p>
            </div>
          </b-col>
          <b-col class="d-flex align-items-center">
            <div class="card__tags">
              <b-badge class="font-weight-normal condition-badge mr-3">{{
                car.advert_classification
              }}</b-badge>
              <b-icon icon="star" aria-hidden="true" :font-scale="1.3"></b-icon>
            </div>
          </b-col>
        </b-row>
      </header>

      <div class="card__body">
        <b-row>
          <b-col>
            <div class="card__specs">
              <span class="card__spec"
                >{{ formatMiles }} {{ car.odometer_units }}</span
              >
              <span class="card__spec--divider"> | </span>
              <span class="card__spec">{{ car.transmission }}</span>
              <span class="card__spec--divider"> | </span>
              <span class="card__spec">{{ car.fuel_type }}</span>
              <span class="card__spec--divider"> | </span>
              <span class="card__spec">{{ car.body_type }}</span>
            </div>
          </b-col>
          <b-col>
            <div class="card__pricing">
              <div class="card__pricing--monthly">
                <p v-show="!!car.monthly_payment">
                  <span>{{ car.monthly_payment }}</span> /mo (PCP)
                </p>
              </div>
              <div class="card__pricing--full d-flex">
                <p class="card__pricing--new mr-2">${{ car.original_price }}</p>
                <p class="card__pricing--old">${{ car.price }}</p>
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
import mercedes from "@/assets/images/mercedes.jpg";
import peugeot from "@/assets/images/peugeot.jpg";
import renault from "@/assets/images/renault.jpg";

export default {
  name: "MobileCarCard",
  components: { Carousel, Slide },
  data() {
    return {
      images: {
        mercedes,
        peugeot,
        renault,
      },
    };
  },
  props: {
    car: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    formatMiles() {
      if (this.car.odometer_value < 1000) return this.car.odometer_value;

      const formated = this.car.odometer_value / 1000;

      return String(formated).split(".")[0] + "k";
    },

    getImages() {
      if (this.images[this.car.make.toLowerCase()]) {
        return this.images[this.car.make.toLowerCase()];
      }
      return Object.entries(this.images)[Math.floor(Math.random() * 3)][1];
    },
  },
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
  margin-bottom: 3rem;
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

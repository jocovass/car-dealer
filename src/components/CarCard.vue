<template>
  <div class="card--outer">
    <div class="card" style="border: none">
      <div v-if="isMobile" class="card__img-slide">
        <carousel :perPage="3" :paginationEnabled="false">
          <slide class="slide" v-for="index in 5" :key="index">
            <img :src="getImages" :alt="car.name" />
          </slide>
        </carousel>
      </div>
      <div v-else class="card__thumbnail">
        <img class="card__thumbnail-img" :src="getImages" :alt="car.name" />
        <div class="card__thumbnail-overlay">
          <div>
            <b-badge class="condition-badge condition-badge--big">{{
              car.advert_classification
            }}</b-badge>
          </div>
          <div>
            <b-badge class="condition-badge"
              >{{ formatMiles }} {{ car.odometer_units }}</b-badge
            >
            <b-badge class="condition-badge">{{ car.transmission }}</b-badge>
            <b-badge class="condition-badge">{{ car.fuel_type }}</b-badge>
            <b-badge class="condition-badge">{{ car.body_type }}</b-badge>
          </div>
        </div>
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
                <p class="card__subtitle">{{ car.name.slice(0, 20) }}...</p>
              </div>
            </b-col>
            <b-col
              class="
                d-flex
                align-items-center
                justify-content-center justify-content-md-end
              "
            >
              <div class="card__tags">
                <b-badge
                  class="
                    condition-badge condition-badge--big
                    d-inline-block d-md-none
                  "
                  >{{ car.advert_classification }}</b-badge
                >
                <b-icon
                  icon="star"
                  aria-hidden="true"
                  :font-scale="1.3"
                ></b-icon>
              </div>
            </b-col>
          </b-row>
        </header>

        <div class="card__body">
          <b-row>
            <b-col class="d-block d-md-none">
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
              <div class="card__pricing text-align-end">
                <div class="card__pricing--monthly">
                  <p v-show="!!car.monthly_payment">
                    <span>{{ car.monthly_payment }}</span> /mo (PCP)
                  </p>
                </div>
                <div
                  class="
                    card__pricing--full
                    d-flex
                    align-items-center
                    justify-content-end justify-content-md-start
                  "
                >
                  <p class="card__pricing--new mr-2">
                    ${{ car.original_price }}
                  </p>
                  <p class="card__pricing--old mr-md-2">${{ car.price }}</p>
                  <p class="valuate__btn d-none d-md-block">
                    Calculate finance
                  </p>
                </div>
              </div>
            </b-col>
          </b-row>
        </div>
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
      isMobile: true,
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
  created() {
    this.checkDeviceSize();
    window.addEventListener("resize", this.checkDeviceSize);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.checkDeviceSize);
  },
  methods: {
    checkDeviceSize() {
      console.log(this.isMobile);
      window.matchMedia("(min-width: 768px)").matches
        ? (this.isMobile = false)
        : (this.isMobile = true);
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
  &--outer {
    max-width: 460px;
    margin: 0 auto 3rem;
    flex-basis: 100%;
  }

  &__thumbnail {
    position: relative;
    border-radius: 20px 20px 0 0;
    overflow: hidden;

    &-overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      padding: 0.7rem;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
  }

  &__title {
    font-size: 0.9rem;
    font-family: $font-family-base;
    font-weight: 400;
    margin-bottom: 0.2rem;
  }

  &__subtitle {
    font-size: 0.75rem;
    color: $text-lighter;
  }

  .condition-badge {
    background-color: $dark-light;
    padding: 0.5em 0.8em;
    border-radius: 8px;
    font-weight: normal;
    font-size: 0.75rem;
    font-weight: 300;
    margin-right: 0.2rem;

    &--big {
      font-weight: 400;
      margin-right: 0.8rem;
    }
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

    .valuate__btn {
      font-weight: 300;
      color: $accent;
    }
  }
}

@include media-breakpoint-up(md) {
  .card {
    &--outer {
      margin: 0;
      margin-bottom: 3rem;
      max-width: 345px;
      padding: 0 10px;
    }
    border-radius: 20px;
    box-shadow: 0px 6px 25px rgba(0, 0, 0, 0.15);

    .condition-badge--big {
      font-size: 1rem;
    }

    &__details {
      padding: 1.2rem 1rem;
    }

    &__title {
      font-size: 1rem;
    }

    &__pricing {
      &--monthly {
        p {
          margin-bottom: 3px;
        }
        span {
          font-size: 1.12rem;
        }
      }

      &--new,
      &--old {
        font-size: 0.9rem;
      }
    }
  }
}
</style>

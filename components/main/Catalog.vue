<template>
  <section class="catalog" aria-labelledby="catalog-title">
    <div class="catalog__container">
      <h2 id="catalog-title" class="catalog__title">КАТАЛОГ АВТО</h2>

      <Swiper
        :modules="[Navigation]"
        :space-between="20"
        :breakpoints="{
          320: { slidesPerView: 1 },
          768: { slidesPerView: 2 },
          1596: { slidesPerView: 4 },
        }"
        @swiper="setSwiperInstance"
        @slide-change="updatePagination"
        id="car-gallery"
      >
        <SwiperSlide
          v-for="(car, index) in cars"
          :key="`${car.model}-${index}`"
          :aria-label="`Модель ${car.model}, комплектация ${car.trim}`"
          role="group"
          aria-roledescription="slide"
        >
          <article class="swiper-slide__content">
            <img
              :src="`/cars/${car.image}`"
              :alt="`${car.model} ${car.trim}`"
              class="swiper-slide__image"
              loading="lazy"
            />
            <div class="swiper-slide__text">
              <h3 class="swiper-slide__title">{{ car.model }}</h3>
              <p class="swiper-slide__discription">{{ car.trim }}</p>

              <footer class="swiper-slide__footer">
                <div>
                  <mark>{{ car.price_per_day }} ₽</mark>
                  /в сутки
                </div>

                <div>график {{ car.schedule }}</div>
              </footer>
            </div>
            <div class="swiper-slide__note">*возможен график 6/1</div>
          </article>
        </SwiperSlide>
      </Swiper>

      <div class="navigation" aria-controls="car-gallery">
        <div class="navigation__counter" aria-live="polite">
          {{ swiperState.currentSlide }} из {{ maxSwipes }}
        </div>

        <div class="navigation__buttons">
          <button
            @click="slidePrev"
            class="navigation__button navigation__button--left"
            :class="{ 'navigation__button--disabled': isBeginning }"
            :disabled="isBeginning"
            aria-label="Предыдущий слайд"
          >
            <svg aria-hidden="true" focusable="false">
              <use xlink:href="/icons.svg#arrow"></use>
            </svg>
          </button>

          <button
            @click="slideNext"
            class="navigation__button"
            :class="{ 'navigation__button--disabled': isEnd }"
            :disabled="isEnd"
            aria-label="Следующий слайд"
          >
            <svg aria-hidden="true" focusable="false">
              <use xlink:href="/icons.svg#arrow"></use>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation } from 'swiper/modules'

import 'swiper/css'
import cars from 'public/cars.json'

const swiperState = ref({
  instance: null,
  currentSlide: 1,
  totalSlides: 0,
  slidesPerView: 1,
})

const maxSwipes = computed(() =>
  Math.max(
    swiperState.value.totalSlides - swiperState.value.slidesPerView + 1,
    1
  )
)

const isBeginning = computed(() => swiperState.value.currentSlide === 1)
const isEnd = computed(() => swiperState.value.currentSlide >= maxSwipes.value)

const setSwiperInstance = (swiper) => {
  swiperState.value = {
    ...swiperState.value,
    instance: swiper,
    totalSlides: swiper.slides.length,
    slidesPerView: swiper.params.slidesPerView,
  }

  swiper.on('resize', () => {
    swiperState.value.slidesPerView = swiper.params.slidesPerView
  })
}

const updatePagination = () => {
  if (swiperState.value.instance) {
    swiperState.value.currentSlide = swiperState.value.instance.activeIndex + 1
  }
}

const slidePrev = () => swiperState.value.instance?.slidePrev()
const slideNext = () => swiperState.value.instance?.slideNext()
</script>

<style lang="scss" scoped>
.catalog {
  background-color: $main-color;
  &__container {
    @include container;
  }
  &__title {
    color: $white-color;
    margin-bottom: 1.5rem;
  }
}

.swiper-slide {
  background: #f0f0f0;
  overflow: hidden;
  box-sizing: border-box;
  border-radius: 20px;
  white-space: pre-line;
  position: relative;

  &__header {
    display: flex;
    justify-content: space-between;
    font-size: 1.25rem;
    height: 50px;
  }

  &__image {
    object-fit: cover;
    width: 100%;
    height: 225px;
  }

  &__text {
    padding: 12px 18px;
  }
  &__title {
    font-size: 1.4rem;
  }
  &__discription {
    font-size: 1.25rem;
  }
  &__footer {
    margin-top: 20px;
    display: flex;
    align-items: baseline;
    justify-content: space-between;

    mark {
      color: $main-color;
      font-size: 1.4rem;
      background: none;
    }
  }
  &__note {
    position: absolute;
    padding: 4px 12px;
    border-bottom-left-radius: 10px;
    background: $white-color;
    color: $text-color;
    right: 0;
    top: 0;
  }
}

.navigation {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-top: 1px solid #e7e7e7;
  padding-top: $section-padding;
  gap: 20px;
  margin-top: $section-padding;

  &__counter {
    font-size: 1.2rem;
    color: #fff;
    min-width: 60px;
    text-align: center;
  }

  &__buttons {
    display: flex;
    gap: 20px;
  }

  &__button {
    width: 40px;
    height: 40px;
    border: 1px solid #fff;
    border-radius: 50%;

    fill: #fff;
    cursor: pointer;
    display: flex;
    transition: opacity 0.3s ease;

    svg {
      height: 100%;
      width: 100%;
    }

    &--left {
      transform: rotate(180deg);
    }

    &--disabled {
      opacity: 0.6;
    }
  }
}
</style>

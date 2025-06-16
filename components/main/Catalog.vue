<template>
  <section class="catalog">
    <div class="catalog__container">
      <h2 class="catalog__title">КАТАЛОГ АВТО</h2>

      <ul class="catalog__list">
        <li 
          v-for="(car, index) in cars" 
          :key="`${car.model}-${index}`" 
          class="catalog__item"
        >
          <article class="card">
            <div class="card__image-wrapper">
              <img
                :src="`/cars/${car.image}`"
                :alt="`${car.model} ${car.trim}`"
                class="card__image"
                loading="lazy"
              />
              <span class="card__note">*возможен график 6/1</span>
            </div>

            <div class="card__content">
              <h3 class="card__title">{{ car.model }}</h3>
              <p class="card__description">{{ car.trim }}</p>

              <footer class="card__footer">
                <div class="card__price">
                  <span class="card__price-value">{{ car.price_per_day }} ₽</span>
                  <span class="card__price-label">/в сутки</span>
                </div>
                <div class="card__schedule">график {{ car.schedule }}</div>
              </footer>
            </div>
          </article>
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup>
import cars from 'public/cars.json'
</script>

<style lang="scss" scoped>
.catalog {
  background-color: $main-color;
  padding: $section-padding 0;

  &__container {
    @include container;
  }

  &__title {
    color: $white-color;
    margin-bottom: 24px;
    font-size: 24px;
    font-weight: 700;
  }

  &__list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    margin: 0;
    padding: 0;
    list-style: none;

    @media (max-width: 1595px) {
      grid-template-columns: repeat(3, 1fr);
    }

    @media (max-width: 1200px) {
      grid-template-columns: repeat(2, 1fr);
    }

    @media (max-width: 767px) {
      grid-template-columns: 1fr;
    }
  }

  &__item {
    margin: 0;
    padding: 0;
  }
}

.card {
  background: $white-color;
  border-radius: 20px;
  overflow: hidden;
  height: 100%;
  display: flex;
  flex-direction: column;

  &__image-wrapper {
    position: relative;
  }

  &__image {
    width: 100%;
    height: 225px;
    object-fit: cover;
    display: block;
  }

  &__note {
    position: absolute;
    top: 0;
    right: 0;
    padding: 4px 12px;
    background: $white-color;
    color: $text-color;
    font-size: 12px;
    border-bottom-left-radius: 10px;
  }

  &__content {
    padding: 12px 18px;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
  }

  &__title {
    font-size: 20px;
    font-weight: 600;
    margin: 0 0 8px 0;
    color: $text-color;
  }

  &__description {
    font-size: 16px;
    margin: 0 0 16px 0;
    color: $text-color;
  }

  &__footer {
    margin-top: auto;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
  }

  &__price {
    &-value {
      color: $main-color;
      font-size: 20px;
      font-weight: 700;
    }

    &-label {
      font-size: 14px;
      color: $text-color;
    }
  }

  &__schedule {
    font-size: 14px;
    color: $text-color;
  }
}
</style>
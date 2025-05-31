<template>
  <section class="banner">
    <div class="banner__container">
      <h1 class="banner__title">Аренда авто в Москве</h1>
      <p class="banner__discription">
        Откройте для себя свободу совместного использования автомобилей с Мицар.
        Гибкие условия бронирования, доступные цены и незабываемые поездки ждут
        вас.
      </p>

      <div class="banner__buttons">
        <NuxtLink to="#about" class="banner__bnt" aria-label="Перейти к о нас"
          >Узнать больше</NuxtLink
        >
        <NuxtLink
          to="#catalog"
          class="banner__bnt banner__bnt--cta"
          aria-label="На главную"
          >Стать водителем</NuxtLink
        >
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style lang="scss" scoped>
.banner {
  height: 600px;
  line-height: 1.2;
  position: relative;
  overflow: hidden;
  background-image: url('/images/banner.png');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  color: #fff;

  &__container {
    padding-block: 50px;
    display: flex;
    flex-direction: column;
    @include container;
    @include tablet {
      justify-content: center;
    }
  }

  &__discription {
    max-width: 600px;
    margin: 16px 0px 32px;
    font-size: 1.5rem;
  }
  &__buttons {
    display: flex;
    flex-direction: column;
    gap: 12px;
    margin-top: auto;
    @include tablet {
      margin-top: 0;
      flex-direction: row;
    }
  }
  &__bnt {
    box-shadow: 0px 10px 10px 0px rgba(15, 16, 17, 0.1);
    border-radius: 12px;
    color: #fff;
    font-size: 1.5rem;
    border: 2px solid white;
    padding: 8px 16px;
    text-align: center;
    @include tablet {
      width: max-content;
    }

    &--cta {
      border: none;
      background: $main-color;
    }
  }
}
</style>

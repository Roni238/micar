<template>
  <section class="advantages">
    <div class="advantages__container">
      <h2 class="advantages__title">НАШИ ПРЕИМУЩЕСТВА</h2>

      <div class="advantages__list">
        <div class="advantages__item" v-for="item in items" :key="item.title">
          <h3 class="advantages__item-title">{{ item.title }}</h3>
          <p class="advantages__item-discription">
            {{ item.discription }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const items = [
  {
    title: 'Огромный выбор автомобилей',
    discription: `От элегантных седанов до просторных кроссоверов.\n\n Выбирайте авто под любой стиль вождения и ситуацию.`,
  },
  {
    title: 'Первый день аренды — бесплатно!',
    discription: `Попробуйте наши авто без риска — первый день аренды за наш счет! \n\n Оцените комфорт и надежность, прежде чем принимать решение.`,
  },
  {
    title: 'Все расходы – на нас',
    discription: `Мы полностью берем на себя техническое обслуживание. \n\n Ремонт, страховка ОСАГО и даже сезонная замена резины.`,
  },
  {
    title: 'Все автомобили с лицензией на перевозку пассажиров',
    discription: `Все машины официально допущены к перевозкам, что гарантирует их безопасность и соответствие всем требованиям законодательства.`,
  },
  {
    title: 'Без ограничений по пробегу',
    discription: `Все километры входят в стоимость аренды. \n\n Платите только за время аренды, а не за расстояние.`,
  },
  {
    title: 'Бустер в каждом авто',
    discription: `Вы можете брать в аренду машину даже для поездок с ребенком. \n\n Безопасность и комфорт – для всех пассажиров!`,
  },
  {
    title: 'Прозрачные партнерские отношения с водителями',
    discription: `Мы ценим каждого клиента и предлагаем понятные, выгодные. Никаких неожиданных списаний – только честные условия. `,
  },
  {
    title: 'Все официально',
    discription: `Mицар – это лицензированный каршеринг. Все договоры, платежи и документы оформляются официально, а наши клиенты получают полную юридическую защищенность.`,
  },
]
</script>

<style lang="scss" scoped>
.advantages {
  background-color: #f9fafb;
  &__container {
    @include container;
  }
  &__title {
    margin-bottom: 1.5rem;
  }

  &__list {
    margin: auto;
    display: grid;
    gap: 16px;
    grid-template-columns: 1fr;
    @include tablet {
      gap: 20px;
      grid-template-columns: repeat(2, 1fr);
    }
    @include desktop {
      grid-template-columns: repeat(4, 1fr);
    }
  }
  &__item {
    padding: 14px;
    border-left: $main-color solid 5px;
    box-shadow: 0px 4px 4px 4px rgba(15, 16, 17, 0.1);
    border-radius: 10px;
    box-sizing: border-box;
    white-space: pre-line;

    @include tablet {
      padding: 18px;
    }
    @include laptop {
      padding: 18px 22px;
    }

    &-discription {
      color: $text-color;
      margin-top: 1rem;
    }
  }
}
</style>

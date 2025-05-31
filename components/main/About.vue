<template>
  <section class="about">
    <div class="about__container">
      <h2 class="about__title">О НАС</h2>
      <div class="about__content">
        <div class="about__discription">
          <p>
            Если вы хотите работать водителем в Москве, иметь гибкий график и
            свободно управлять своим временем и доходом – сотрудничество с
            автопарком ООО «Мицар» станет отличной возможностью для заработка!
          </p>
          <p>
            Наша компания ООО "Мицар" работает на рынке в сфере аренды авто с
            2018 года. За это время мы смогли заслужить доверие и уважение среди
            водителей. Парк «Мицар» ориентируется, в первую очередь, на
            дружеских отношениях с водителем. Мы не стремимся сдать автомобиль в
            аренду и забыть о проблемах водителя! Наша команда полностью
            участвует в рабочем процессе водителя, помогая работать на себя в
            первую очередь, и только потом на автомобиль. Подтверждением тому
            является большое количество не сменяемых водителей, которые работают
            с нами уже долгие годы, а многие и со дня открытия. Автопарк ООО
            "Мицар" гарантирует профессиональный и строгий подход к своей
            работе, что позволяет водителям ездить на надежных, своевременно и
            качественно обслуживаемых автомобилях. Мы делаем все возможное,
            чтобы в нашей команде работали вежливые и доброжелательные
            сотрудники, а также опытные и квалифицированные водители.
          </p>
          <p>
            Вы ищите автомобиль для работы, тогда мы сделаем все, чтоб это
            работа приносила Вам удовольствие!
          </p>
        </div>

        <div class="about__stats">
          <div class="stat">
            <strong class="stat__title">5+</strong>
            <p class="stat__discription">Лет на рынке</p>
          </div>
          <div class="stat">
            <strong class="stat__title">1500+</strong>
            <p class="stat__discription">
              Довольных <br />
              клиентов
            </p>
          </div>
          <div class="stat">
            <strong class="stat__title">50+</strong>
            <p class="stat__discription">Авто в наличии</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style lang="scss" scoped>
.about {
  &__container {
    @include container;
  }

  &__content {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    @include laptop {
      display: grid;
      grid-template-columns: 1fr 1fr;
    }
  }

  &__title {
    margin-bottom: 1.5rem;
  }

  &__discription p {
    color: $text-color;
    text-indent: 20px;
  }
  &__stats {
    display: flex;
    justify-content: space-evenly;
    @include tablet {
      align-items: center;
    }
  }
}

.stat {
  text-align: center;

  &__title {
    color: $main-color;
    font-size: 1.5rem;
    margin-bottom: 10px;
  }

  &__discription {
    font-weight: bold;
  }
}
</style>

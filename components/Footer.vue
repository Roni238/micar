<template>
  <footer class="footer">
    <div class="footer__container">
      <UiLogo class="footer__logo" />

      <div class="footer__content">
        <div class="footer__contacts">
          <BaseLink :link="'phone'" class="footer__link footer__link--phone">
            Телефон для связи: <br />
          </BaseLink>

          <ul class="footer__social">
            <li>
              <BaseLink :link="'whatsapp'" class="footer__link" />
            </li>
            <li>
              <BaseLink :link="'telegram'" class="footer__link" />
            </li>
          </ul>
        </div>

        <div class="footer__requisites">
          <p>
            Юридический адрес: <br />
            115035 г. Москва ул. Космодамианская наб. Д.4/22 к.Б пом.8Н.
          </p>
          <p class="footer__address-title">
            Мы находимся: <br />
            г.Москва вн.тер.г. муниципальный округ печатники, ул. Шоссейная д.90
            стр.17
          </p>
          <p>ИНН: 9723045017</p>
          <p>ОГРН: 1187746380040</p>
        </div>
      </div>
    </div>
    <p class="footer__copyright">© 2025 ООО «Мицар». Все права защищены.</p>
  </footer>
</template>

<script setup>
import BaseLink from '@/components/ui/BaseLink.vue'
</script>

<style lang="scss" scoped>
.footer {
  padding-block: $section-padding;
  font-size: 0.875rem;
  color: $white-color;
  line-height: 1.5;
  background-color: $dark-blue-color;

  &__container {
    display: flex;
    flex-direction: column;
    @include container;
  }

  &__content {
    display: flex;
    flex-direction: column;
    @include tablet {
      flex-direction: row-reverse;
      justify-content: space-between;
    }
  }
  &__logo {
    margin-bottom: 12px;
    @include tablet {
      margin: 0px;
    }
  }

  &__contacts {
    padding-block: 12px;
    border-block: 1px solid $main-color;
    display: flex;
    gap: 0.5rem;

    @include tablet {
      border: none;
      flex-direction: column;
    }
  }

  &__social {
    justify-content: end;
    gap: 0.5rem;
  }

  &__link {
    color: $white-color;
    fill: $white-color;
    transition: color 0.2s ease, fill 0.2s ease;

    &:hover {
      color: $main-color;
      fill: $main-color;
    }

    &--phone {
      margin-right: auto;
      font-weight: bold;
      @include tablet {
        text-align: end;
      }
    }
  }

  &__requisites {
    padding: 12px 0px;
  }

  &__copyright {
    text-align: center;
    margin-top: 16px;
  }
}
</style>

<template>
  <div
    v-if="isOpen"
    class="dropdown"
    role="dialog"
    aria-modal="true"
    :aria-hidden="!isOpen"
    @keydown.esc="closeDropdown"
  >
    <transition name="dropdown" appear>
      <div class="dropdown__content">
        <nav class="nav" aria-label="Основное меню">
          <ul class="nav__list">
            <li>
              <NuxtLink to="/#about" @click="closeDropdown"> О нас </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/#catalog" @click="closeDropdown">
                Каталог авто
              </NuxtLink>
            </li>
          </ul>
        </nav>

        <div class="contacts">
          <BaseLink :link="'whatsapp'" class="contacts__link" />
          <BaseLink :link="'telegram'" class="contacts__link" />

          <BaseLink
            :link="'phone'"
            class="contacts__link contacts__link--phone"
          />
        </div>
      </div>
    </transition>
    <div class="dropdown__overlay" @click="closeDropdown" aria-hidden="true" />
  </div>
</template>

<script setup>
import BaseLink from '@/components/ui/BaseLink.vue'

const props = defineProps({
  isOpen: Boolean,
})

const emit = defineEmits(['close'])

const closeDropdown = () => emit('close')
</script>

<style scoped lang="scss">
.dropdown {
  width: 100%;
  font-size: 1.1rem;

  @include tablet {
    display: none;
  }
  &__overlay {
    position: fixed;
    inset: 60px 0 0 0;
    z-index: -1;
    background-color: rgba(0, 0, 0, 0.5);
  }

  &__content {
    background: white;
    box-shadow: 0px 10px 10px 0px rgba(15, 16, 17, 0.1);
    padding: 20px;
  }
}

.contacts {
  display: flex;
  align-items: center;
  gap: 16px;
  padding-top: 16px;
  border-top: 1px solid #eee;

  &__link {
    color: $main-color;
    fill: $main-color;
    &--phone {
      margin-left: auto;
    }
  }
}

.nav {
  margin-bottom: 24px;
  &__list {
    flex-direction: column;
    gap: 16px;
  }
}

.dropdown-enter-active,
.dropdown-leave-active {
  transition: all 0.3s ease;
}

.dropdown-enter-from,
.dropdown-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>

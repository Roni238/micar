<template>
  <header class="header">
    <div class="header__container">
      <UiLogo class="header__logo" />

      <nav class="nav">
        <ul>
          <li>
            <NuxtLink class="nav__link" to="/#about">О нас</NuxtLink>
          </li>
          <li>
            <NuxtLink class="nav__link" to="/#catalog">Каталог авто</NuxtLink>
          </li>
        </ul>
      </nav>
      <div class="contacts">
        <BaseLink :link="'whatsapp'" />
        <BaseLink :link="'telegram'" />
        <BaseLink :link="'phone'" />
      </div>

      <button
        aria-label="Меню"
        aria-expanded="false"
        class="mobile-nav-btn"
        @click="toggleDropdown"
      >
        <svg>
          <use href="/icons.svg#sidebar-icon" />
        </svg>
      </button>
    </div>

    <DropdownMenu :is-open="isDropdownOpen" @close="closeDropdown" />
  </header>
</template>
<script setup>
import BaseLink from '@/components/ui/BaseLink.vue'

const isDropdownOpen = ref(false)

const toggleDropdown = () => {
  isDropdownOpen.value = !isDropdownOpen.value
  document.body.classList.toggle('no-scroll', isDropdownOpen.value)
}
const closeDropdown = () => {
  isDropdownOpen.value = false
  document.body.classList.remove('no-scroll')
}
</script>

<style lang="scss" scoped>
a {
  font-size: 1.1rem;
}
.mobile-nav-btn {
  background: none;
  border: none;

  @include tablet {
    display: none;
  }
  svg {
    height: 30px;
    width: 30px;
    stroke: $main-color;
  }
}

.header {
  z-index: 100;
  height: 60px;
  width: 100%;
  box-shadow: 0px 10px 10px 0px rgba(15, 16, 17, 0.15);
  position: sticky;
  background-color: #fff;
  top: 0px;
  @include tablet {
    height: 70px;
  }
  &__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 15px;
    @include container;
  }
  &__logo {
    margin-right: auto;
  }
}

.nav {
  display: none;
  @include tablet {
    display: block;
  }
  ul {
    display: flex;
    gap: 20px;
    align-items: center;
  }
  &__link {
    &:hover {
      color: $main-color;
      transition: color 0.2s ease;
    }
  }
}
.contacts {
  display: none;
  @include tablet {
    display: flex;
    align-items: center;
    gap: 15px;
  }

  a {
    fill: $main-color;
    color: $main-color;
  }
}
</style>

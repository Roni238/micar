<template>
  <NuxtLink to="#banner" class="logo" aria-label="На главную">
    
    <svg>
      <use href="/icons.svg#logo-icon" />
    </svg>
  </NuxtLink>
</template>

<script setup></script>

<style lang="scss" scoped>

.logo svg {
  width: 407px;
  height: 377;
  @include laptop {
    width: 146px;
    height: 40px;
  }
}
</style>

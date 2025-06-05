<template>
  <NuxtLink to="#banner" class="logo" aria-label="На главную">
    <h1>МИЦАР</h1>
    <!-- <svg>
      <use href="/icons.svg#logo-icon" />
    </svg> -->
  </NuxtLink>
</template>

<script setup></script>

<style lang="scss" scoped>
h1 {
  color: $main-color;
}
.logo svg {
  width: 104px;
  height: 24px;
  @include laptop {
    width: 146px;
    height: 40px;
  }
}
</style>

<template>
  <a
    :href="contacts[link].href"
    :aria-label="contacts[link].label"
    target="_blank"
    rel="noopener noreferrer"
  >
    <svg v-if="contacts[link].icon" aria-hidden="true" focusable="false">
      <title>{{ contacts[link].title }}</title>
      <use :href="`/icons.svg#${contacts[link].icon}`" />
    </svg>

    <template v-else>
      <slot />
      {{ contacts[link].title }}
    </template>
  </a>
</template>

<script setup>
import contacts from 'public/contacts.json'

const { link } = defineProps({
  link: {
    type: String,
    required: true,
  },
})
</script>

<style lang="scss" scoped>
svg {
  fill: inherit;
  height: 40px;
  width: 40px;
}
</style>

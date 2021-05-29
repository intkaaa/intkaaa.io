<template>
  <NuxtLink :to="'entry/' + id" class="item">
    <p class="item__title" v-text="title" />
  </NuxtLink>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'WorksListItem',
  props: {
    id: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      required: true,
    },
    role: {
      type: String,
      required: true,
    },
  },
})
</script>

<style lang="scss" scoped>
.item {
  display: grid;
  gap: $xxs;
  text-decoration: none;

  &__title,
  &__role {
    line-height: 1;
  }

  &__title {
    color: $text-base;
    font-size: 22px;
    font-weight: bold;

    @include tablet-ls {
      font-size: 28px;
    }
  }

  &__role {
    color: $text-pale;
    font-size: 12px;

    @include tablet-ls {
      font-size: 14px;
    }
  }
}
</style>

<template>
  <NuxtLink :to="'entry/' + id" class="item">
    <time class="item__date" v-text="date" />
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
    date: {
      type: String,
      required: true,
    },
    title: {
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

  &__date {
    margin-top: $xxxs;
    color: $text-base;
    font-size: 12px;
    line-height: 1;
    letter-spacing: 0.05rem;

    @include tablet-ls {
      font-size: 14px;
    }
  }

  &__title {
    color: $text-base;
    font-size: 16px;
    font-weight: $bold;
    line-height: 1.8;

    @include tablet-ls {
      font-size: 18px;
    }
  }
}
</style>

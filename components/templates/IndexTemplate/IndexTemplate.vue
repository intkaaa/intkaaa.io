<template>
  <div class="index">
    <ul class="index__list list">
      <li v-for="(item, key) in items" :key="key" class="list__item item">
        <WorksListItem :id="item.id" :title="item.title" class="item__card" />
      </li>
    </ul>
  </div>
</template>

<script>
import Vue from 'vue'
import WorksListItem from '~/components/molecules/WorksListItem/WorksListItem.vue'

export default Vue.extend({
  name: 'IndexTemplate',
  components: {
    WorksListItem,
  },
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
})
</script>

<style lang="scss" scoped>
.list {
  display: grid;
  gap: $l;
  list-style-type: none;

  @include tablet-ls {
    gap: $xl;
  }
}
</style>

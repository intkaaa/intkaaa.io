<template>
  <ContentSection id="writing" heading="Writing" class="writing">
    <ul class="writing__list list">
      <li v-for="(item, key) in items" :key="key" class="list__item item">
        <WorksListItem
          :id="item.id"
          :title="item.title"
          :date="$dateFns.format(item.publishedAt, 'yyyy.MM.dd')"
          class="item__card"
        />
      </li>
    </ul>
  </ContentSection>
</template>

<script>
import Vue from 'vue'
import WorksListItem from '~/components/molecules/WorksListItem/WorksListItem.vue'
import ContentSection from '~/components/organisms/ContentSection/ContentSection.vue'

export default Vue.extend({
  name: 'IndexWriting',
  components: {
    WorksListItem,
    ContentSection,
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
.writing {
  &__list {
    margin-top: $m;

    @include tablet-ls {
      margin-top: initial;
    }
  }
}

.list {
  display: grid;
  list-style-type: none;

  &__item {
    padding: $s 0;
    border-top: 1px dotted $gray-500;

    @include tablet-ls {
      padding: $m 0;

      &:first-of-type {
        border-top: none;
      }
    }
  }
}

.item {
  &__link {
    font-size: 18px;
    color: $text-base;
    text-decoration: none;
  }
}
</style>

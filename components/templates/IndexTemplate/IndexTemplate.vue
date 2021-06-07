<template>
  <div class="index">
    <IndexHero class="index__hero" />
    <IndexWriting :items="items" class="index__writing" />
    <IndexAbout class="index__about" />
  </div>
</template>

<script>
import Vue from 'vue'
import IndexHero from '~/components/templates/IndexTemplate/IndexHero/IndexHero.vue'
import IndexWriting from '~/components/templates/IndexTemplate/IndexWriting/IndexWriting.vue'
import IndexAbout from '~/components/templates/IndexTemplate/IndexAbout/IndexAbout.vue'

export default Vue.extend({
  name: 'IndexTemplate',
  components: {
    IndexHero,
    IndexWriting,
    IndexAbout,
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
.index {
  &__hero {
    margin-top: $xs;
    margin-bottom: $xl;

    @include tablet-ls {
      margin-top: $l;
      margin-bottom: 60px;
    }
  }
}
</style>

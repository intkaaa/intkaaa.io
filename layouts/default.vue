<template>
  <div id="top" class="layout">
    <AppHeader class="layout__header" />
    <Nuxt class="layout__content" />
    <AppFooter class="layout__footer" />
  </div>
</template>

<script>
import Vue from 'vue'
import AppHeader from '~/components/organisms/AppHeader/AppHeader.vue'
import AppFooter from '~/components/organisms/AppFooter/AppFooter.vue'

export default Vue.extend({
  components: {
    AppHeader,
    AppFooter,
  },
})
</script>

<style lang="scss" scoped>
.layout {
  padding: 0 $m;
  background-color: $primary;

  @include tablet-ls {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    padding: calc(60px - #{$m}) 60px 0;
  }

  &__header {
    z-index: 1;
    position: sticky;
    top: 0;
  }

  &__content {
    margin-bottom: $m;
  }

  &__footer {
    @include tablet-ls {
      margin-top: auto;
    }
  }
}
</style>

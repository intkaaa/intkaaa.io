<template>
  <div class="layout">
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
  background-color: $white;

  @include tablet-ls {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    padding: 0 $xxxl;
  }

  &__header {
    position: sticky;
    top: 0;
    width: 100vw;
    margin-left: -#{$m};
    padding: $xl $m $l;

    @include tablet-ls {
      margin-left: -#{$xxxl};
      padding: $xxxl $xxxl $xxl;
    }
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

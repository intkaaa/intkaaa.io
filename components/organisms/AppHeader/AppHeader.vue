<template>
  <header class="header">
    <NuxtLink to="/" class="header__link">
      <AppLogo class="header__logo" />
    </NuxtLink>
  </header>
</template>

<script>
import Vue from 'vue'
import AppLogo from '~/components/atoms/AppLogo.vue'

export default Vue.extend({
  name: 'AppHeader',
  components: {
    AppLogo,
  },
})
</script>

<style lang="scss" scoped>
.header {
  &__link {
    display: inline-block;
    text-decoration: none;
  }
}
</style>

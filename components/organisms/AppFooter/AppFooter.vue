<template>
  <footer class="footer">
    <small class="footer__copyright">2021 ©️ intkaaa.io</small>
    <NuxtLink v-scroll-to="'#top'" to class="footer__top">Back to top</NuxtLink>
  </footer>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'AppFooter',
})
</script>

<style lang="scss" scoped>
.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: $m 0;

  @include tablet-ls {
    padding: $l 0;
  }

  &__copyright,
  &__top {
    display: block;
    font-size: 14px;
    color: $text-base;
    text-decoration: none;
  }

  &__top {
    width: 74px;
  }
}

.list {
  display: flex;
  align-items: center;
  gap: $m;
  list-style-type: none;
}

.item {
  &__link {
    font-size: 14px;
    color: $text-base;
    text-decoration: none;
  }
}
</style>

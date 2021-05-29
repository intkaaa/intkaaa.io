<template>
  <span class="logo">intkaaa I/O</span>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'AppLogo',
})
</script>

<style lang="scss">
.logo {
  display: block;
  font-size: 24px;
  font-weight: bold;
  color: $text-base;
  line-height: 1;

  @include tablet-ls {
    font-size: 28px;
  }
}
</style>

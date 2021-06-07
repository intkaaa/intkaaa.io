<template>
  <div class="logo">
    <img src="./logo.svg" alt="I/O" class="logo__image" />
    intkaaa I/O
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'AppLogo',
})
</script>

<style lang="scss">
.logo {
  display: flex;
  align-items: center;
  gap: $s;
  font-size: 16px;
  font-weight: bold;
  color: $text-base;
  line-height: 1;

  @include tablet-ls {
    font-size: 20px;
  }

  &__image {
    width: 40px;
    height: 40px;

    @include tablet-ls {
      width: 52px;
      height: 52px;
    }
  }
}
</style>

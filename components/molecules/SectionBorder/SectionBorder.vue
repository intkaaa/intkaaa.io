<template>
  <div class="border">
    <hr class="border__item" />
    <hr class="border__item" />
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'SectionBorder',
})
</script>

<style lang="scss" scoped>
.border {
  display: flex;
  align-items: center;

  @include tablet-ls {
    display: grid;
    grid-template-columns: 33% 1fr;
    gap: $xxxl;
  }

  &__item {
    width: 100%;
    height: 1px;
    margin: 0;
    border: none;
    background-color: $black;
  }
}
</style>

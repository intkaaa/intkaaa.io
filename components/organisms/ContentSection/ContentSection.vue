<template>
  <section class="section">
    <SectionBorder class="section__border" />
    <h2 class="section__heading">{{ heading }}</h2>
    <div class="section__body body">
      <slot />
    </div>
  </section>
</template>

<script>
import Vue from 'vue'
import SectionBorder from '~/components/molecules/SectionBorder/SectionBorder.vue'

export default Vue.extend({
  name: 'ContentSection',
  components: {
    SectionBorder,
  },
  props: {
    heading: {
      type: String,
      required: true,
    },
  },
})
</script>

<style lang="scss" scoped>
.section {
  position: relative;
  display: grid;
  grid-template-areas:
    'border'
    'heading'
    'body';

  @include tablet-ls {
    grid-template-areas:
      'border border'
      'heading body';
    grid-template-columns: 33% 1fr;
    grid-template-rows: 1px 1fr;
    align-items: start;
    column-gap: $xxxl;
  }

  &__border {
    grid-area: border;

    @include tablet-ls {
      position: sticky;
      top: 100px;
      width: 100%;
    }
  }

  &__heading {
    grid-area: heading;
    padding-top: $m;
    font-size: 18px;
    font-weight: normal;
    line-height: 1;
    text-align: center;

    @include tablet-ls {
      position: sticky;
      top: 100px;
      padding: $m 0;
      font-size: 32px;
      text-align: left;
    }
  }

  &__body {
    grid-area: body;
  }
}
</style>

<template>
  <section class="hero">
    <h2 class="hero__heading heading">
      Organize,<br />design <span class="heading__amp">&amp;</span> code.
    </h2>
    <p class="hero__description description">
      主に日々の仕事や生活などで得た知見や気づきを発散し、<br
        class="description__br"
      />思考整理することを目的とした個人サイトです。
    </p>
  </section>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexHero',
})
</script>

<style lang="scss" scoped>
.hero {
  &__heading {
    transform: translateX(-3px);

    @include tablet-ls {
      margin-top: -#{$xs};
      transform: translateX(-6px);
    }
  }

  &__description {
    margin-top: $m;

    @include tablet-ls {
      margin-top: $l;
    }
  }
}

.heading {
  font-size: 50px;
  font-weight: normal;
  line-height: 1.1;

  @include tablet-ls {
    font-size: 100px;
  }

  &__amp {
    font-size: 42px;

    @include tablet-ls {
      font-size: 88px;
    }
  }
}

.description {
  font-size: 14px;

  @include tablet-ls {
    font-size: 16px;
  }

  &__br {
    display: none;

    @include tablet-ls {
      display: block;
    }
  }
}
</style>

<template>
  <article class="article">
    <header class="article__header header">
      <h1 class="header__title">{{ item.title }}</h1>
    </header>
    <!-- eslint-disable-next-line vue/no-v-html -->
    <div class="article__body body" v-html="$md.render(item.body)" />
  </article>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import Prism from '~/plugins/prism'

export default Vue.extend({
  name: 'WorksIdLandingPage',
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://intkaaa.microcms.io/api/v1/entry/${params.id}`,
      {
        headers: { 'X-API-KEY': process.env.API_KEY },
      }
    )
    return {
      item: data,
    }
  },
  data() {
    return {
      items: [],
    }
  },
  mounted() {
    Prism.highlightAll()
  },
})
</script>

<style lang="scss" scoped>
.article {
  width: 100%;
  max-width: $max-width;
  margin: 0 auto;

  &__body {
    margin-top: $l;
  }
}

.header {
  display: grid;
  gap: $s;

  &__title {
    font-size: 28px;
    font-weight: bold;
    line-height: 1.6;

    @include tablet-ls {
      font-size: 44px;
    }
  }
}

.body {
  ::v-deep {
    img {
      width: 100vw;
      margin: $xl 0;
      margin-left: -#{$m};

      @include tablet-ls {
        width: 100%;
        margin: $xxxl 0;
        margin-left: initial;
      }
    }

    p,
    ul,
    ol {
      margin: $xl 0;

      @include tablet-ls {
        margin: $xxxl 0;
      }
    }

    ul,
    ol {
      padding-left: $m;
    }

    h2,
    h3,
    h4,
    h5,
    h6 {
      margin-bottom: -#{$xl};
      font-size: 18px;
      font-weight: bold;

      @include tablet-ls {
        margin-bottom: -#{$xxxl};
      }
    }
  }
}
</style>

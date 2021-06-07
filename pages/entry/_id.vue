<template>
  <div class="entry">
    <SectionBorder class="entry__border" />
    <aside class="entry__toc toc">
      <NuxtLink class="toc__back back" to="/">
        <img src="~/assets/icons/back.svg" alt="back" class="back__icon" />
        Back
      </NuxtLink>
      <h2 class="toc__heading">Table of contents</h2>
      <ul class="toc__list list">
        <li
          v-for="item in toc"
          :key="item.id"
          :class="`list__item item item--${item.name}`"
        >
          <NuxtLink
            v-scroll-to="{ el: `#${item.id}`, offset: -156 }"
            to
            class="item__link"
          >
            {{ item.text }}
          </NuxtLink>
        </li>
      </ul>
    </aside>
    <article class="entry__article article">
      <NuxtLink class="article__back back" to="/">
        <img src="~/assets/icons/back.svg" alt="back" class="back__icon" />
        Back
      </NuxtLink>
      <header class="article__header header">
        <time class="header__date">
          {{ $dateFns.format(item.publishedAt, 'yyyy.MM.dd') }}
        </time>
        <h1 class="header__title">{{ item.title }}</h1>
      </header>
      <aside class="article__toc toc">
        <h2 class="toc__heading">Table of contents</h2>
        <ul class="toc__list list">
          <li
            v-for="item in toc"
            :key="item.id"
            :class="`list__item item item--${item.name}`"
          >
            <NuxtLink
              v-scroll-to="{ el: `#${item.id}`, offset: -156 }"
              to
              class="item__link"
            >
              {{ item.text }}
            </NuxtLink>
          </li>
        </ul>
      </aside>
      <!-- eslint-disable-next-line vue/no-v-html -->
      <div class="article__body body" v-html="$md.render(item.body)" />
    </article>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import cheerio from 'cheerio'
import Prism from '~/plugins/prism'
import SectionBorder from '~/components/molecules/SectionBorder/SectionBorder.vue'

export default Vue.extend({
  name: 'WorksIdLandingPage',
  components: {
    SectionBorder,
  },
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://intkaaa.microcms.io/api/v1/entry/${params.id}`,
      {
        headers: { 'X-API-KEY': process.env.API_KEY },
      }
    )
    const $ = cheerio.load(data.body)
    const headings = $('h1, h2, h3').toArray()
    const toc = headings.map((d) => {
      return {
        text: d.children[0].data,
        id: d.attribs.id,
        name: d.name,
      }
    })
    return {
      item: data,
      toc,
    }
  },
  data() {
    return {
      items: [],
    }
  },
  mounted() {
    Prism.highlightAll()
    // const $ = cheerio.load(body)
    // const headings = $('h2, h3').toArray()
    // const toc = headings.map((data) => ({
    //   text: data.children[0].data,
    //   id: data.attribs.id,
    //   name: data.name,
    // }))
  },
})
</script>

<style lang="scss" scoped>
.entry {
  position: relative;
  display: grid;

  @include tablet-ls {
    grid-template-areas:
      'border border'
      'toc article';
    grid-template-columns: 33% 1fr;
    grid-template-rows: 1px 1fr;
    align-items: start;
    column-gap: $xxxl;
    margin-top: calc(60px - #{$m});
  }

  &__border {
    @include mobile {
      display: none;
    }

    @include tablet-ls {
      grid-area: border;
      position: sticky;
      top: 100px;
      width: 100%;
    }
  }

  &__toc {
    grid-area: toc;
    display: none;

    @include tablet-ls {
      display: block;
      position: sticky;
      top: 100px;
      padding-top: $m;
    }
  }

  &__article {
    grid-area: article;

    @include tablet-ls {
      padding-top: $m;
    }
  }
}

.toc {
  &__back,
  &__heading {
    display: block;
    font-size: 14px;
    font-weight: normal;
    color: $text-base;
  }

  &__heading {
    margin-top: $s;
  }

  &__list {
    margin-top: $xxxs;
  }
}

.back {
  display: grid;
  grid-template-columns: 16px 1fr;
  align-items: center;
  gap: $xxxs;
  font-size: 14px;
  font-weight: normal;
  color: $text-base;
  text-decoration: none;

  &__icon {
    width: 16px;
    height: 16px;
  }
}

.list {
  list-style-type: none;
}

.item {
  &--h3 {
    padding-left: $s;
  }

  &__link {
    display: block;
    font-size: 14px;
    color: $text-base;
  }
}

.article {
  width: 100%;

  &__back,
  &__toc {
    @include tablet-ls {
      display: none;
    }
  }

  &__header {
    margin-top: $xxs;

    @include tablet-ls {
      margin-top: initial;
    }
  }

  &__toc {
    margin-top: $s;
    padding: 1px $m $s;
    border-radius: $radius-small;
    background-color: $secondary;
  }

  &__body {
    margin-top: $l;
  }
}

.header {
  display: grid;

  &__date {
    font-size: 14px;
  }

  &__title {
    font-size: 24px;
    font-weight: bold;
    line-height: 1.6;
    transform: translateX(-2px);

    @include tablet-ls {
      font-size: 28px;
      transform: translateX(-4px);
    }
  }
}

.body {
  ::v-deep {
    * {
      white-space: initial;
      font-size: 14px;
      font-weight: $normal;

      @include tablet-ls {
        font-size: 16px;
      }
    }

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
      margin-top: $xl;
      margin-bottom: -#{$m};
      font-weight: bold;

      @include tablet-ls {
        margin-top: $xxxl;
        margin-bottom: -#{$xl};
      }
    }

    h2 {
      font-size: 20px;

      @include tablet-ls {
        font-size: 24px;
      }
    }

    h3 {
      font-size: 18px;

      @include tablet-ls {
        font-size: 20px;
      }
    }

    h4,
    h5,
    h6 {
      font-size: 16px;

      @include tablet-ls {
        font-size: 18px;
      }
    }

    a {
      color: $text-base;
    }

    blockquote {
      margin-top: -#{$m};
      padding-left: $m;
      border-left: 4px solid $secondary;
      border-radius: 2px;
      color: $text-pale;

      @include tablet-ls {
        margin-top: -#{$xl};
      }
    }
  }
}
</style>

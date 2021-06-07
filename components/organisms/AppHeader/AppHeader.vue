<template>
  <header class="header">
    <NuxtLink to="/" class="header__link">
      <AppLogo class="header__logo" />
    </NuxtLink>

    <nav class="header__nav nav">
      <ul class="nav__list list">
        <li class="list__item item">
          <NuxtLink v-scroll-to="'#top'" to class="item__link">Top</NuxtLink>
        </li>
        <li class="list__item item">
          <NuxtLink v-scroll-to="'#writing'" to class="item__link"
            >Writing</NuxtLink
          >
        </li>
        <li class="list__item item">
          <NuxtLink v-scroll-to="'#about'" to class="item__link"
            >About</NuxtLink
          >
        </li>
        <li class="list__item item">
          <NuxtLink v-scroll-to="'#updates'" to class="item__link"
            >Updates</NuxtLink
          >
        </li>
      </ul>
    </nav>

    <div class="header__theme theme">
      <img src="~/assets/icons/theme.svg" alt="icon" class="theme__icon" />
    </div>
  </header>
</template>

<script>
import Vue from 'vue'
import AppLogo from '~/components/atoms/AppLogo/AppLogo.vue'

export default Vue.extend({
  name: 'AppHeader',
  components: {
    AppLogo,
  },
})
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100vw;
  margin-left: -#{$m};
  padding: $m;

  @include tablet-ls {
    display: grid;
    grid-template-columns: 181px 1fr 181px;
    margin-left: -60px;
    padding: $m 60px;
  }

  &::before {
    content: '';
    z-index: 0;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    backdrop-filter: blur(32px);
    opacity: 0;
    transition: 0.3s;
  }

  @include is-pointer-device {
    &:hover {
      &::before {
        opacity: 1;
      }
    }
  }

  &__link,
  &__nav,
  &__theme {
    position: relative;
  }

  &__link {
    display: inline-block;
    text-decoration: none;
  }

  &__nav {
    display: none;

    @include tablet-ls {
      display: block;
      margin: auto;
    }
  }
}

.list {
  display: flex;
  align-items: center;
  gap: $xxxl;
  list-style-type: none;
}

.item {
  &__link {
    display: block;
    font-size: 14px;
    color: $text-base;
    text-decoration: none;
  }
}

.theme {
  display: flex;
  justify-content: flex-end;

  &__icon {
    width: 24px;
    height: 24px;
  }
}
</style>

<template>
  <ContentSection id="about" heading="About">
    <div class="body__profile profile">
      <div class="profile__image image">
        <img src="./profile.png" alt="icon" class="image__item" />
      </div>
      <div class="profile__content content">
        <h3 class="content__heading">イノウエタカヒト</h3>
        <p class="content__text">
          東京を拠点に、UI/UXデザイナー・フロントエンドエンジニアとして活動しています。
        </p>
        <ul class="content__social-list social-list">
          <li class="social-list__item social-item">
            <a href="https://twitter.com/intkaaa" class="social-item__link"
              >Twitter</a
            >
          </li>
          <li class="social-list__item social-item">
            <a href="https://note.com/intkaaa" class="social-item__link"
              >note</a
            >
          </li>
        </ul>
      </div>
    </div>
  </ContentSection>
</template>

<script>
import Vue from 'vue'
import ContentSection from '~/components/organisms/ContentSection/ContentSection.vue'

export default Vue.extend({
  name: 'IndexAbout',
  components: {
    ContentSection,
  },
})
</script>

<style lang="scss" scoped>
.profile {
  display: grid;
  padding: $m 0;

  @include tablet-ls {
    grid-template-columns: 120px 1fr;
    gap: $l;
  }

  &__image {
    display: block;
    width: 120px;
    margin: auto;
  }

  &__content {
    padding-top: $xs;
    text-align: center;

    @include tablet-ls {
      text-align: left;
    }
  }
}

.content {
  &__social-list {
    margin-top: $xxxs;
  }
}

.social-list {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: $m;
  list-style-type: none;

  @include tablet-ls {
    justify-content: flex-start;
  }
}

.social-item {
  &__link {
    display: block;
    font-size: 14px;
    color: $text-base;
    text-decoration: none;
  }
}
</style>

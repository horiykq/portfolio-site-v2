<template>
  <div class="m-psBlogPostCard">
    <ps-link :href="path" class="m-psBlogPostCard__outer">
      <article class="m-psBlogPostCard__inner">
        <ps-image
          v-if="thumbnail !== null"
          class="m-psBlogPostCard__thumbnail"
          :src="thumbnail"
          alt="サムネイル"
        />
        <div class="m-psBlogPostCard__information">
          <header class="m-psBlogPostCard__cardHeader">
            <ps-time
              class="m-psBlogPostCard__publishedAt"
              :string-time="publishedAt"
              :seperated-by-slash="false"
            />
            <span class="m-psBlogPostCard__category">{{ category }}</span>
          </header>
          <main class="m-psBlogPostCard__cardContents">
            <h2 class="m-psBlogPostCard__title">{{ title }}</h2>
          </main>
          <footer class="m-psBlogPostCard__cardFooter">
            <ps-arrow />
          </footer>
        </div>
      </article>
    </ps-link>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import PsArrow from '~/components/atoms/ps-arrow.vue';
import PsImage from '~/components/atoms/ps-image.vue';
import PsLink from '~/components/atoms/ps-link.vue';
import PsTime from '~/components/atoms/ps-time.vue';
export default Vue.extend({
  components: { PsImage, PsLink, PsTime, PsArrow },
  props: {
    title: {
      type: String,
      default: '',
    },
    thumbnail: {
      type: String,
      default: null,
    },
    path: {
      type: String,
      default: '/',
    },
    publishedAt: {
      type: String,
      default: '',
    },
    category: {
      type: String,
      default: '',
    },
  },
});
</script>

<style lang="scss" scoped>
$block: '.m-psBlogPostCard';
#{$block} {
  display: inline-block;
  width: 100%;
  padding: 32px 0;
  @include mq_pc {
    padding: 0 32px 64px 32px;
  }
  &__outer {
    width: 100%;
    border-radius: 24px;
    overflow: hidden;
    color: $color-default-black;
    box-shadow: 0 10px 25px 0 rgba(0, 0, 0, 0.25);
    @include hover {
      opacity: 0.92;
      box-shadow: 0 20px 50px 0 rgba(0, 0, 0, 0.25);
    }
  }
  &__inner {
    display: inline-block;
    width: 100%;
  }
  &__thumbnail {
    object-fit: cover;
  }
  &__information {
    display: inline-block;
    width: 100%;
    padding: 24px;
    @include mq_pc {
      padding: 32px;
    }
  }
  &__cardHeader {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    @include mq_pc {
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
    }
  }
  &__publishedAt {
    font-family: $en-font;
    font-weight: 400;
    @include font-size(1.8);
  }
  &__category {
    font-weight: 300;
    border: 1px solid $color-border-black;
    padding: 4px 16px;
    border-radius: 28px;
    margin: 8px 0;
    @include mq_pc {
      margin: 0;
    }
  }
  &__cardContents {
    display: inline-block;
    width: 100%;
  }
  &__title {
    font-weight: 600;
    margin: 16px 0;
    @include font-size(2.4);
  }
  &__cardFooter {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    width: 100%;
  }
}
</style>

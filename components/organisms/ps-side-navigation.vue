<template>
  <div
    :class="
      isShowOnlyPc
        ? 'o-psSideNavigation o-psSideNavigation__pcOnly'
        : 'o-psSideNavigation'
    "
  >
    <nav class="o-psSideNavigation__navigation">
      <ps-top-link :is-active="browsedPagePath === pagePaths.top" />
      <ps-side-links :browsed-page-path="browsedPagePath" />
    </nav>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import PsTopLink from '../atoms/ps-top-link.vue';
import PsSideLinks from '../molecules/ps-side-links.vue';
import pagePaths from '~/config/page-paths';
export default Vue.extend({
  components: { PsTopLink, PsSideLinks },

  props: {
    browsedPagePath: {
      type: String,
      required: true,
    },
    isShowOnlyPc: {
      type: Boolean,
      default: false,
    },
  },

  data() {
    return {
      pagePaths,
    };
  },
});
</script>

<style lang="scss" scoped>
$block: '.o-psSideNavigation';
#{$block} {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  @include mq_pc {
    width: 320px;
    height: 100vh;
  }
  &__pcOnly {
    @include mq_sp {
      display: none;
    }
    @include mq_tablet {
      display: none;
    }
  }
  &__navigation {
    display: inline-block;
    width: calc(100% - 96px);
  }
}
</style>

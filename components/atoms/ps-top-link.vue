<template>
  <ps-link
    :class="isActive ? 'a-psTopLink a-psTopLink__isActive' : 'a-psTopLink'"
    :href="pagePaths.top"
  >
    <div class="a-psTopLink__inner">
      Portfolio
      <ps-responsive-break :is-show-pc="true" />
      of
      <br />
      Kaito Horiuchi
    </div>
  </ps-link>
</template>

<script lang="ts">
import Vue from 'vue';
import PsLink from './ps-link.vue';
import PsResponsiveBreak from './ps-responsive-break.vue';
import pagePaths from '~/config/page-paths';
export default Vue.extend({
  components: { PsLink, PsResponsiveBreak },

  props: {
    isActive: {
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
$block: '.a-psTopLink';
#{$block} {
  display: inline-block;
  width: 100%;
  padding-left: 12px;
  border-left: 2px solid $color-white;
  @include font-size(2);
  @include mq_pc {
    @include font-size(2.4);
  }
  &__isActive {
    border-left: 2px solid $color-default-blue;
  }
  &__inner {
    display: inline-block;
    text-transform: uppercase;
    font-family: $en-font;
    color: $color-default-black;
    @include hover {
      color: $color-dark-blue;
    }
  }
}
</style>

<template>
  <div :class="cssClasses"><slot /></div>
</template>

<script lang="ts">
export default {
  name: 'VueGridItem',
  props: {
    fill: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    cssClasses() {
      const classes = [this.$style.gridItem];

      if (this.fill) {
        classes.push(this.$style.fill);
      }

      return classes;
    },
  },
};
</script>

<style lang="scss" module>
@import '~@/app/shared/design-system';

.gridItem {
  flex-basis: 100%;
  justify-content: center;
  padding: 0 ($screen-phone-gutter * 0.25);
  margin: auto;

  @include mediaMin(tabletPortrait) {
    flex: 1;
    padding: 0 ($screen-tablet-portrait-gutter * 0.25);

    &.fill {
      flex: 1 1 100%;
    }
  }

  @include mediaMin(tabletLandscape) {
    padding: 0 ($screen-tablet-landscape-gutter * 0.25);
  }

  @include mediaMin(smallDesktop) {
    padding: 0 ($screen-small-desktop-gutter * 0.25);
  }

  @include mediaMin(largeDesktop) {
    padding: 0 ($screen-large-desktop-gutter * 0.25);
  }
}
</style>

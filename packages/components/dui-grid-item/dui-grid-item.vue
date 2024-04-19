<template>
  <view
    :class="cls"
    :style="{
      width: grid.cols ? 100 / grid.cols + '%' : '100%',
      marginLeft: `${grid.colGap / 2}px`,
      marginRight: `${grid.colGap / 2}px`,
      flexShrink: `${grid.colGap ? 1 : 0}`,
    }">
    <slot />
  </view>
</template>

<script setup>
import { computed, inject } from 'vue'
import { isBoolean } from '../../helper/is'

const grid = inject('dui-grid-props')

const prefixCls = 'dui-grid-item'

const cls = computed(() => [
  prefixCls,
  {
    [`${prefixCls}-border`]: grid.border,
    [`${prefixCls}-hover`]: isBoolean(grid.clickEffect) && grid.clickEffect,
  },
])
</script>

<style lang="scss" scoped>
@import '../../style/index.scss';
.dui-grid-item {
  display: flex;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
  color: $color-text;

  &-border {
    border: 1px solid $color-border;
  }

  &-hover {
    &:active {
      background-color: $color-bg-secondary;
      border-radius: $border-radius-small;
    }
  }
}
</style>

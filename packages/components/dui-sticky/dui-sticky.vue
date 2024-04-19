<template>
  <view :id="`${prefixCls}-content`" :class="cls" :style="{ top: offsetTop + 'px', paddingBottom: offsetTop + 'px' }">
    <slot />
  </view>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  /**
   * 吸顶时与顶部的距离
   */
  offsetTop: {
    type: Number,
    default: 0,
  },

  /**
   * z-index 层级
   */
  zIndex: {
    type: Number,
    default: 1000,
  },
})

const prefixCls = 'dui-sticky'

const cls = computed(() => [prefixCls])
</script>

<style lang="scss" scoped>
.dui-sticky {
  position: sticky;
  z-index: v-bind(zIndex);
}
</style>

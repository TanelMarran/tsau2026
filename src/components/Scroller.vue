<script setup lang="ts">
import { useElementBounding, useElementSize } from '@vueuse/core';
import { computed, provide, useTemplateRef } from 'vue';

const refScrollTrack = useTemplateRef('scroll-track')
const refScrollCart = useTemplateRef('scroll-cart')

const props = defineProps<{
    height: number
}>()

const boundingBox = useElementBounding(refScrollTrack)
const size = useElementSize(refScrollTrack)
const sizeCart = useElementSize(refScrollCart)

const computeScrollProgress = () => {
    if (!size.height.value || !sizeCart.height.value) {
        return 0
    }

    return Math.max(0.0, Math.min(1.0, Math.abs(-boundingBox.top.value) / (size.height.value - sizeCart.height.value)))
}

const scrollProgress = computed<number>(computeScrollProgress)

provide('scroll-progress', scrollProgress)
</script>

<template>
  <div class="scroller">
    <div
      ref="scroll-track"
      class="scroller__track"
      :style="{ height: props.height + 'px' }"
    >
      <div
        ref="scroll-cart"
        class="scroller__cart"
      >
        <slot />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.scroller__track {
    position: relative;
}

.scroller__cart {
    position: sticky;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    top: 0;
}
</style>
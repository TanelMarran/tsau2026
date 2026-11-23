<script lang="ts" setup>
import { inject } from 'vue';

interface ParallaxerProps {
    offset?: number;
    speed?: number;
}

const props = withDefaults(defineProps<ParallaxerProps>(), {
    offset: 0,
    speed: 1
})

const scrollProgressInjection = inject('scroll-progress', 0);
</script>

<template>
  <div
    ref="parallax-root"
    class="parallaxer"
  >
    <div
      class="parallaxer__transform"
      :style="{ transform: `translateY(${(props.offset + scrollProgressInjection * props.speed * -1000)}px)`}"
    >
      <slot />
    </div>
  </div>
</template>

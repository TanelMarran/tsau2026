<script lang="ts" setup>
import { useElementBounding, useElementSize } from '@vueuse/core';
import { inject, useTemplateRef } from 'vue';

interface ParallaxerProps {
    offset?: number;
    speed?: number;
}

const parallaxRootRef = useTemplateRef('parallax-root')
const boundingBox = useElementBounding(parallaxRootRef)

const props = withDefaults(defineProps<ParallaxerProps>(), {
    offset: 0,
    speed: 1
})

const scrollProgressInjection = inject('scroll-progress', 0);
</script>

<template>
    <div class="parallaxer" ref="parallax-root">
        <div class="parallaxer__transform" :style="{ transform: `translateY(${(props.offset + scrollProgressInjection * speed * -1000)}px)`}">
            <slot></slot>
        </div>
    </div>
</template>
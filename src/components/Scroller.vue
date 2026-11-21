<script setup lang="ts">
import { useElementSize, useScroll } from '@vueuse/core';
import { computed, onMounted, onUnmounted, provide, Ref, ref, useTemplateRef, watch } from 'vue';

const refScrollTarget = useTemplateRef('scroll-target')

const props = defineProps<{

}>()

const scroll = useScroll(refScrollTarget)
const size = useElementSize(refScrollTarget)

const scrollProgress = computed<number>(() => (scroll.y.value) / size.height.value)

provide('scroll-progress', scrollProgress)
</script>

<template>
<div class="scroller">
    <div class="scroller__track" ref="scroll-target">
        TextScroller
    </div>
</div>
</template>
<script lang="ts" setup>
import { inject, Ref, watch } from 'vue';


interface GsapAnimatorProps {
    timeline: GSAPTimeline
}

const props = withDefaults(defineProps<GsapAnimatorProps>(), {
})

const scrollProgressInjection = inject<Ref<number>>('scroll-progress')

watch(() => scrollProgressInjection, () => {
    if (scrollProgressInjection) {
        props.timeline.seek(scrollProgressInjection?.value)
    }
})
</script>

<template>
    <slot></slot>
</template>
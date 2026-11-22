<script lang="ts" setup generic="TItem">
import gsap from 'gsap';
import { computed, inject, Ref, watch } from 'vue';

export type TextScrollerItemProps = {
    open: boolean
}

export type TextScrollerProps<TItem> = {
    flickStrength?: number
    visibilityRange?: number
    items: TItem[]
}

const props = withDefaults(defineProps<TextScrollerProps<TItem>>(), {
    flickStrength: 5,
    visibilityRange: 3
})

const scrollProgressInjection = inject<Ref<number>>('scroll-progress')
const scrollProgress = computed<number>(() => (scrollProgressInjection?.value ?? 0))

const dotCount = computed(() => props.items.length)

const currentOpenIndex = computed(() => Math.min(dotCount.value - 1, Math.floor(((scrollProgress.value) * (dotCount.value)))))

const getLocalProgress = (_index: number) => {
    const step = 1.0 / (dotCount.value)
    const minValue = step * (_index)
    const domainSize = step

    return Math.min(1, Math.max(0, scrollProgress.value - minValue) / (domainSize))
}

const animateFlick = (direction: 'up' | 'down') => {
    const directionSign = direction == 'up' ? 1 : -1

    gsap.killTweensOf('.text-scroller')
    gsap.to('.text-scroller', { y: directionSign * props.flickStrength, duration: 0, ease: 'elastic.out'})
    gsap.to('.text-scroller', { y: 0, duration: 1, ease: 'elastic.out'})
}

watch(currentOpenIndex, (value, oldValue) => {
    animateFlick(value < oldValue ? 'up' : 'down')
})

defineExpose({
    animateFlick
})
</script>

<template>
    <div class="text-scroller">
        <template v-for="(item, index) in props.items" :key="index">
            <slot 
                name="item"
                v-bind="item"
                :visible="Math.abs(index - currentOpenIndex) < props.visibilityRange"
                :open="index == currentOpenIndex" 
                :dotScrollProgress="getLocalProgress(index - 1)"
            ></slot>
        </template>
    </div>
</template>

<style lang="scss">
.text-scroller {
    display: flex;
    flex-direction: column;
    gap: 16px;
}
</style>

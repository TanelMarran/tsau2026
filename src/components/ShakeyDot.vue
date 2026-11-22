<script lang="ts" setup>
import { computed } from 'vue';

interface ShakeyDotProps {
isShaking?: boolean
fillAmount?: number
fillScale?: number
}


const props = withDefaults(defineProps<ShakeyDotProps>(), {
    fillAmount: 0,
    isShaking: false,
    fillScale: 1,
})

const clampedFillAmount = computed(() => Math.max(0, Math.min(1, props.fillAmount)))
const transformScale = computed(() => {
    return (1.0 - props.fillScale) + clampedFillAmount.value * props.fillScale;
})
</script>

<template>
    <div 
        class="shakey-dot"
    >
        <div class="shakey-dot__fill-border">
            <div class="shakey-dot__fill" :style="{ transform: `scale(1, ${transformScale})`}"></div>
        </div>
    </div>
</template>

<style lang="scss">
.shakey-dot {
    position: relative;
    width: 25px;
    height: 25px;
    border: 4px solid var(--color-rose-50);
    border-radius: 50%;
}

.shakey-dot__fill-border {
    position: absolute;
    left: 2px;
    right: 2px;
    top: 2px;
    bottom: 2px;
    border-radius: 50%;
    overflow: hidden;
}

.shakey-dot__fill {
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    right: 0;
    transform: scale(1, 0);
    transform-origin: top center;
    background: var(--color-rose-50);
}
</style>
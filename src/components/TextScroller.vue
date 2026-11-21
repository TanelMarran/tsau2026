<script lang="ts" setup generic="TItem">
import { computed, inject, Ref } from 'vue';

export type TextScrollerItemProps = {
    open: boolean
}

export type TextScrollerProps<TItem> = {
    items: TItem[]
}

const props = defineProps<TextScrollerProps<TItem>>()

const scrollProgress = inject<Ref<number>>('scroll-progress')

const currentOpenIndex = computed(() => Math.floor((scrollProgress?.value ?? 0) * props.items.length))

</script>

<template>
    <div class="text-scroller">
        <template v-for="(item, index) in props.items" :key="index">
            <slot name="item" v-bind="item" :open="index == currentOpenIndex"></slot>
        </template>
    </div>
</template>

<style lang="scss">

</style>

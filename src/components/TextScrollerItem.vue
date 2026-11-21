<script lang="ts" setup>

export interface TextScrollerItemProps {
}

const props = defineProps<TextScrollerItemProps>()
const isOpen = defineModel('is-open')

</script>

<template>
    <div 
        class="text-scroller-item"
        :class="{
            'is-open': isOpen
        }"
    >
        <div class="text-scroller-item__open">
            <slot></slot>
        </div>
        <div class="text-scroller-item__closed">
            <slot name="closed">
                <div class="text-scroller-item__closed-icon"></div>
            </slot>
        </div>
    </div>
</template>
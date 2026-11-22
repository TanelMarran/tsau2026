<script lang="ts" setup>

export interface TextScrollerItemProps {
    isOpen: boolean
}

const props = defineProps<TextScrollerItemProps>()

</script>

<template>
    <div 
        class="text-scroller-item"
        :class="{
            'is-open': props.isOpen
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

<style lang="scss">
.text-scroller-item {
    display: flex;
    align-items: center;
    justify-content: center;
}

.text-scroller-item__open {
    opacity: 0;
    position: fixed;

    .text-scroller-item.is-open & {
        opacity: 1;
        position: static;
    }
}

.text-scroller-item__closed {
    opacity: 1;

    .text-scroller-item.is-open & {
        opacity: 0;
        position: fixed;
    }
}

.text-scroller-item__closed-icon {
    width: 16px;
    height: 16px;
    margin: 8px;
    background: white;
    border-radius: 50%;
}
</style>
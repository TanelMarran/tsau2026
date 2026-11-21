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
        <div v-show="props.isOpen" class="text-scroller-item__open">
            <slot></slot>
        </div>
        <div v-show="!props.isOpen" class="text-scroller-item__closed">
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

.text-scroller-item__closed-icon {
    width: 16px;
    height: 16px;
    margin: 8px;
    background: white;
    border-radius: 50%;
}
</style>
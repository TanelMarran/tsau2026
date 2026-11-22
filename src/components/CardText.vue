<script setup lang="ts">

export interface CardTextProps {
    title?: String,
    body: String
}

const props = defineProps<CardTextProps>()

</script>

<template>
    <div class="card-text py-4">
        <div class="text-block">
            <h1 v-if="title" class="card-text__title text-center">
                {{ props.title }}
            </h1>
            <div class="card-text__body text-2xl text-center">
                {{ props.body }}
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">

export interface CardTextProps {
    title?: String,
    body: String
}

const props = defineProps<CardTextProps>()

</script>

<template>
    <div class="card-text">
        <h1 v-if="body" class="card-text__title text-center">
            {{ props.title }}
        </h1>
        <div class="card-text__body">
            {{ props.body }}
        </div>
    </div>
</template>
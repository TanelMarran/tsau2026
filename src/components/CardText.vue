<script setup lang="ts">

export interface CardTextProps {
    title?: String,
    body: String
}

const props = defineProps<CardTextProps>()

</script>

<template>
    <div class="card-text">
        <div class="text-center">
            <div v-if="title">
                <h1 class="card-text__title text-center mx-auto inline-block mb-4">
                    {{ props.title }}
                </h1>
            </div>
            <p class="card-text__body text-2xl text-center inline whitespace-pre-line">
                {{ props.body }}
            </p>
        </div>
    </div>
</template>
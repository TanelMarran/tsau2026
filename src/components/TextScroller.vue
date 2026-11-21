<script lang="ts" setup>
import { inject } from 'vue';


export interface TextScrollerItem {
    title?: String
    body: String
}

const scrollProgress = inject('scroll-progress', 0)

</script>

<template>
    <div class="text-scroller">
    </div>
</template>
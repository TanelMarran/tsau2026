<script setup lang="ts">
import TextScroller from '../components/TextScroller.vue';

</script>

<template>
    <Scroller>
        <TextScroller>
            <TextScrollerItem>
                <template #title>
                    Heips! 
                </template>
                <template #body>
                    Annan teada, et minu viimaseks tööpäevaks PLAYs jääb 19.12.2026.
                </template>
            </TextScrollerItem>
        </TextScroller>
    </Scroller>
</template>

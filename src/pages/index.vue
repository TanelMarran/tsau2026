<script setup lang="ts">
import { CardTextProps } from '../components/CardText.vue';
import TextScroller from '../components/TextScroller.vue';

const items: CardTextProps[] = [
    {
        title: 'Heips!',
        body: 'Annan märku, et minu viimane tööpäev gotoAndPlays on 19.12.2026.'
    },
    {
        body: 'Okei nii hull see kah pole. Aga ma lahkun küll päris sügavasse vette.'
    },
    {
        body: 'Olen avastanud, et mulle hirmsalt meeldib oma käte ja taibuga maailmaid luua.'
    }
]


</script>

<template>
    <Scroller
        :height="2400 * 4"
    >
        <TextScroller
            class="index__text-scroller"
            :items="items"
        >
            <template #item="{ open, ...props }">
                <TextScrollerItem
                    :isOpen="open"
                >
                    <CardText
                        v-bind="props"
                        :isOpen="false"
                    />
                </TextScrollerItem>
            </template>
        </TextScroller>
    </Scroller>
</template>

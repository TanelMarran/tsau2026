<script setup lang="ts">
import { CardTextProps } from '../components/CardText.vue';
import TextScroller from '../components/TextScroller.vue';

const items: CardTextProps[] = [
    {
        title: 'Heips',
        body: 'Tahan teile kõigile teada anda, et minu viimane tööpäev gotoAndPlays on 19.12.2026'
    },
    {
        body: 'Veidi kurb on seda kirjutada — te kõik väga meeldite mulle'
    },
    {
        body: 'Loodan enesekeskselt, et teil on veidi kurb seda lugeda kah — et ma sarnaselt täitsa meeldin teile'
    },
    {
        body: 'Otsuseni tõi mind üks konka täis igasugu erinevaid teemasid,'
    },
    {
        body: 'kuid suurim neist oli see:'
    },
    {
        body: 'Ma armastan mänguarendust!'
    },
    {
        body: 'Mõned ehk teavad, et arendan hobikorras üht arvutimängu nimega "Letters Past"'
    },
    {
        body: 'Ta on väga kallis mulle. Olen temaga koos lugematult palju asju teinud viimase 2 aasta jooksul:'
    },
    {
        body: 'Joonistanud ja programmeerinud ja nokitsenud ja kirjutanud ja heliloonud ja parandanud ja nutnud ja karjunud ja naernud ja higistanud'
    },
    {
        body: '...ja kus on alles lõbu! Võtab täitsa sõnatuks. Ma tahan veel.'
    },
    {
        body: 'Ma tahan veel haamriga vehkida'
    }
]


</script>

<template>
    <Scroller
        class="px-8"
        :height="2400 * 2"
    >
        <TextScroller
            class="index__text-scroller max-w-160"
            :items="items"
        >
            <template #item="{ open, dotScrollProgress, visible: itemVisible, ...props }">
                <TextScrollerItem
                    :isOpen="open"
                >
                    <template #default>
                        <CardText
                            v-bind="props"
                            :isOpen="false"
                        />
                    </template>
                    <template #closed>
                        <ShakeyDot
                            :fillAmount="(dotScrollProgress)"
                        ></ShakeyDot>
                    </template>
                </TextScrollerItem>
            </template>
        </TextScroller>
    </Scroller>
</template>

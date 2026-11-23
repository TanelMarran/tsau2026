<script setup lang="ts">
import { CardTextProps } from '../components/CardText.vue';
import TextScroller from '../components/TextScroller.vue';

import.meta.glob('../assets/images/export/*.png', {
  import: 'default',
  eager: true
})

const items: CardTextProps[] = [
    {
        title: 'Heips!',
        body: 'Tahan teile kõigile teada anda,\n et minu viimaseks tööpäevaks gotoAndPlays jääb 19.12.2026.'
    },
    {
        body: 'Seda on kurb kirjutada —'
    },
    {
        body: 'Te kõik olete mulle väga meeldima hakanud!'
    },
    {
        body: 'Ja mulle meeldib mõelda, et tunne on vastastikune.'
    },
    {
        body: 'Aga vahest ei piisa headest töösuhetest,'
    },
    {
        body: 'vahest jääb hing,\nsee ahnuskott,\nmillegi muu järgi veel unistama...'
    },
    {
        body: 'Otsuseni tõi mind konka täis põhjuseid,'
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
        body: 'Ta on väga kallis mulle.'
    },
    {
        body: 'Temaga koos olen joonistanud ja programmeerinud ja kirjutanud ja heliloonud ja nutnud ja naernud,'
    },
    {
        body: '...ja kus on alles lõbu!\nVõtab täitsa sõnatuks.'
    },
    {
        body: 'Ma ainult seda teha tahakski:'
    },
    {
        body: 'Luua miskit, et siis see miski saaks luua mind.'
    },
    {
        body: 'Nüüd siis ma lõpuks võtan selle julguse kokku\n ja lähen püüan teada saada,'
    },
    {
        body: 'kas mul on võimalik elada,\ntehes seda mida ma armastan?'
    },
    {
        body: 'Loodetavasti pole vastus liiga sügaval vee all.'
    },
    {
        body: 'Aitäh teile toreda töökoha eest!'
    },
    {
        body: 'Olete olnud parimad kolleegid,\nkeda üks poiskene soovida saab.'
    }
]


</script>

<template>
    <Scroller
        class="px-8"
        :height="2400 * 5"
    >
        <TextScroller
            class="index__text-scroller max-w-160 z-10"
            :visibilityRange="4"
            :items="items"
        >
            <template #item="{ open, dotScrollProgress, visible: itemVisible, isScrolledPast, ...props }">
                <TextScrollerItem
                    class="index__scroller-item"
                    :class="{
                        'index__scroller-item--current': open,
                        'index__scroller-item--minimized': isScrolledPast
                    }"
                    :isOpen="open"
                >
                    <template #default>
                        <CardText
                            v-bind="props"
                            :class="{ 'py-4': open }"
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
        <Parallaxer class="absolute bottom-16 left-1/12 z-0" :speed=".5" :offset="-100">
            <img src="../assets/images/export/tsaukitsau2.png" alt="alt text" width="300px">
        </Parallaxer>
        <Parallaxer class="absolute right-1/12 top-16 z-0" :speed="-1" :offset="50">
            <img src="../assets/images/export/tsaukitsau1.png" alt="alt text" width="250px">
        </Parallaxer>
        <Parallaxer class="absolute left-3/12 top-16 z-0" :speed="1" :offset="1000">
            <img src="../assets/images/export/tsaukitsau3.png" alt="alt text" width="300px">
        </Parallaxer>
        <Parallaxer class="absolute left-2/12 top-16 z-0" :speed="2" :offset="1200">
            <img src="../assets/images/export/tsaukitsau4.png" alt="alt text" width="200px">
        </Parallaxer>
        <Parallaxer class="absolute right-1/5 top-16 z-0" :speed="-2" :offset="0">
            <img src="../assets/images/export/tsaukitsau5.png" alt="alt text" width="500px">
        </Parallaxer>
        <Parallaxer class="absolute right-1/12 top-16 z-0" :speed="12" :offset="4000">
            <img src="../assets/images/export/tsaukitsau6.png" alt="alt text" width="500px">
        </Parallaxer>
        <Parallaxer class="absolute right-1/12 top-16 z-0" :speed="9" :offset="4000">
            <img src="../assets/images/export/tsaukitsau7.png" alt="alt text" width="500px">
        </Parallaxer>
        <Parallaxer class="absolute right-1/12 top-16 z-0" :speed="-9" :offset="-9000">
            <img src="../assets/images/export/tsaukitsau8.png" alt="alt text" width="500px">
        </Parallaxer>
        <Parallaxer class="absolute right-1/12 top-16 z-0" :speed="-12" :offset="-9000">
            <img src="../assets/images/export/tsaukitsau8.png" alt="alt text" width="500px">
        </Parallaxer>
        <Parallaxer class="absolute -left-1/12 top-16 z-0" :speed="2" :offset="1500 * 1.3">
            <img src="../assets/images/export/tsaukitsau10.png" alt="alt text" width="800px">
        </Parallaxer>
    </Scroller>
</template>

<style lang="scss">
@keyframes animIndexPop {
    0% {
        transform: scaleX(2);
    }

    0% {
        transform: scaleX(1);
    }
}

.index__scroller-item {
    margin-bottom: 0;
}

.index__scroller-item--current {
    transform: scaleX(1);
}

.index__scroller-item--minimized {
    h1, p {
        background-color: var(--color-red-50);
        line-height: 1;
    }
}
</style>
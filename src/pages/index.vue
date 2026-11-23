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

const footerData = {
    text: 'Selle hüvastijätu on toonud teile Tanel, kes pole enam päris see sama Tanel, kes ta oli 6 aastat tagasi. Lehe arenduseks kulus: 1 nädalavahetus, 1 telefon, 1 temust ostetud telefonistatiiv, 1 energiajook, 1 tobipaus, 2 kätt, 1 pea, 0 Claude tokenit.',
}


</script>

<template>
  <Scroller
    class="px-8"
    :height="2400 * 5"
  >
    <TextScroller
      class="index__text-scroller max-w-160 z-10"
      :visibility-range="4"
      :items="items"
    >
      <template #item="{ open, dotScrollProgress, isScrolledPast, ...props }">
        <TextScrollerItem
          class="index__scroller-item"
          :class="{
            'index__scroller-item--current': open,
            'index__scroller-item--minimized': isScrolledPast
          }"
          :is-open="open"
        >
          <template #default>
            <CardText
              v-bind="props"
              :class="{ 'py-4': open }"
            />
          </template>
          <template #closed>
            <ShakeyDot
              :fill-amount="(dotScrollProgress)"
            />
          </template>
        </TextScrollerItem>
      </template>
    </TextScroller>
    <Parallaxer
      class="absolute bottom-16 right-4/16 -ml-16 z-0 pointer-events-none"
      :speed="-3.6"
      :offset="-1900"
    >
      <img
        src="../assets/images/export/arendus.JPG"
        alt="Ma arendan"
        :width="200"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute bottom-16 right-1/16 -ml-16 z-0 pointer-events-none"
      :speed="3"
      :offset="1400"
    >
      <img
        src="../assets/images/export/letters.jpg"
        alt="Letters past"
        :width="600"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute bottom-16 right-1/12 z-0 pointer-events-none"
      :speed="3"
      :offset="-100"
    >
      <img
        src="../assets/images/export/sunset.JPG"
        alt="See oli tehtud šotimaal"
        :width="400"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute bottom-16 left-1/12 z-0 pointer-events-none"
      :speed=".5"
      :offset="-100"
    >
      <img
        src="../assets/images/export/tsaukitsau2.png"
        alt="mulle hiljuti väga meeldinud kollaaž"
        width="300px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute left-3/12 top-16 z-0 pointer-events-none"
      :speed="1"
      :offset="1000"
    >
      <img
        src="../assets/images/export/tsaukitsau3.png"
        alt="ja seda veebilehel kasutada oli vahva"
        width="300px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute left-2/12 top-16 z-0 pointer-events-none"
      :speed="2"
      :offset="1200"
    >
      <img
        src="../assets/images/export/tsaukitsau4.png"
        alt="Mul on neid alt tekste veits rohkem, kui mul miskit kirjutada siia on"
        width="200px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute right-1/5 top-16 z-0 pointer-events-none"
      :speed="-2"
      :offset="0"
    >
      <img
        src="../assets/images/export/tsaukitsau5.png"
        alt="ma suuresti sattusin selle disaini otsa kogemata"
        width="500px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute right-1/12 top-16 z-0 pointer-events-none"
      :speed="12"
      :offset="4000"
    >
      <img
        src="../assets/images/export/tsaukitsau6.png"
        alt="Üldine mõte oli, et mida ma tahan teha,"
        width="500px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute right-1/12 top-16 z-0 pointer-events-none"
      :speed="9"
      :offset="4000"
    >
      <img
        src="../assets/images/export/tsaukitsau7.png"
        alt="ja siis nokitsesin ja suund muutus"
        width="500px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute right-1/12 top-16 z-0 pointer-events-none"
      :speed="-9"
      :offset="-9000"
    >
      <img
        src="../assets/images/export/tsaukitsau8.png"
        alt="Alguses mõtlesin üldse, et taust tuleb must!"
        width="500px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute right-1/12 top-16 z-0 pointer-events-none"
      :speed="-12"
      :offset="-9000"
    >
      <img
        src="../assets/images/export/tsaukitsau8.png"
        alt="Aga mulle täitsa meeldib see kipitav sinine"
        width="500px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute -left-1/12 top-16 z-0 pointer-events-none"
      :speed="2"
      :offset="1500 * 1.4"
    >
      <img
        src="../assets/images/export/tsaukitsau10.png"
        alt="On meeldejääv:)"
        width="800px"
      >
    </Parallaxer>
    <Parallaxer
      class="absolute left-0 right-0 bottom-0 z-[-1] -mx-8 pointer-events-none "
      :speed="2.5"
      :offset="1700 * 1.8"
    >
      <div class="index__water-wrapper">
        <div class="index__water" />
      </div>
      <div class="index__water-background" />
    </Parallaxer>
  </Scroller>
  <Footer
    class="zindex-2 relative max-w-[480px] mx-auto"
    v-bind="footerData"
  />
</template>

<style lang="scss">
@keyframes slide {
  0% {
    transform: translate3d(0, 0, 0);
  }
  100% {
    transform: translate3d(-1920px, 0, 0); /* The image width */
  }
}

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

.index__water {
    left: 0;
    width: 1920px * 2;
    height: 210px;

    background-image: url('../assets/images/export/wave.png');
    background-position: center top;
    background-repeat: repeat-x;

    animation: slide 8s infinite linear;
}

.index__water-wrapper {
    overflow: hidden;
    width: 100%;
}

.index__water-background {
    width: 100%;
    height: 800px;
    background-color: #0451e0;
}
</style>

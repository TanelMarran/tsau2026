<script lang="ts" setup>
import ughAudio from '../assets/ugh.m4a';
import {useTemplateRef} from 'vue';

const modelValue = defineModel<boolean>({default: false})

const audioRef = useTemplateRef<HTMLAudioElement>('audio-player')

const playSound = () => {
  if (audioRef.value) {
    audioRef.value.play()
  }
}

</script>

<template>
  <div class="language-picker max-w-50 text-right p-4">
    <div>Language picker:</div>
    <ul>
      <li>
        <button :class="{ 'is-current': modelValue}" @click="modelValue = true">Eesti keel</button>
      </li>
      <li>
        <button :class="{ 'is-current': !modelValue}" @click="modelValue = false">Evridiki</button>
      </li>
      <li>
        <button :class="{ 'is-current': !modelValue}" @click="playSound()">Juku</button>
        <audio :src="ughAudio" ref="audio-player"></audio>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
button {
    cursor: pointer;
    animation: alert 1s infinite;
    animation-timing-function: step-start;
    text-decoration: underline;

    &:hover {
        animation: none;
        text-decoration: none;
    }

    &:active {
        animation: none;
    }

  &.is-current {
    text-decoration: none;
  }
}
</style>

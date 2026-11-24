<script lang="ts" setup>

const props = withDefaults(defineProps<{
    text: string,
  // eslint-disable-next-line vue/require-default-prop
    items?: string[]
}>(), {})

</script>

<template>
  <footer
    class="footer flex justify-center py-4 w-full"
    text="text"
  >
    <div class="flex flex-col w-full text-sm max-w-[480px]">
      <p
        v-if="text"
        class="text-center whitespace-pre-wrap"
        :style="{ 'line-height': 1.05, opacity: .8 }"
      >
        {{ props.text }}
        <a class="underline hover:no-underline" href="https://github.com/TanelMarran/tsau2026" target="_blank">Github</a>.
      </p>
      <ul
        v-if="props.items"
        class="flex flex-col flex-wrap max-h-[7rem] gap-x-4 whitespace-pre-wrap"
      >
        <li
          v-for="item in props.items"
          :key="item"
        >
          {{ item }}
        </li>
      </ul>
    </div>
  </footer>
</template>

<style lang="scss">
.footer {
  background: #0451e0;

  @media screen and (min-width: 1200px) {
    margin-top: -120px;
    background: transparent;
  }
}
</style>

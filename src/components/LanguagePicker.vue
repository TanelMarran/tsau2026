<script lang="ts" setup>

const modelValue = defineModel<boolean>({default: false})
</script>

<template>
  <div class="language-picker max-w-50 text-right">
    <div>Language picker:</div>
    <ul>
      <li>
        <button @click="modelValue = true">Eesti keel</button>
      </li>
      <li>
        <button @click="modelValue = false">Evridiki</button>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
button {
    border: 1px solid darkblue;
    padding: 0 8px;
    background: gray;
    cursor: pointer;
    animation: alert 1s infinite;
    animation-timing-function: step-start;

    &:hover {
        animation: none;
        background: darkgray;
    }

    &:active {
        animation: none;
        background: rgb(131, 131, 131);
    }
}
</style>

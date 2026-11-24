<script lang="ts" setup>
import image1 from "../assets/images/export/isthisyou.png";
import image2 from "../assets/images/export/me.png";

const modelValue = defineModel<boolean>({default: false})
</script>

<template>
    <div class="language-picker max-w-50 text-right">
        <img :src="(modelValue ? image1 : image2)" alt="is this you?">
        <template v-if="modelValue">
            <div>Is your name Evridiki?</div>
            We have some concerning news for you.
        </template>
        <template v-else>
            <div>Pole Evridiki?</div>
            Mis sa siin teed!?
        </template>
        <button class="mt-3" @click="modelValue = !modelValue">{{ modelValue ? 'CLICK HERE!' : 'MINE TAGASI' }}</button>
    </div>
</template>

<style lang="scss" scoped>
@keyframes alert {
    0% {
        background-color: gray;
    }

    49% {
        background-color: gray;
    }
    50% {
        background-color: red;
    }

    100% {
        background-color: red;
    }
}

.language-picker {
    position: absolute;
    top: 32px;
    right: 0;
    background: gray;
    padding: 8px;
}

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
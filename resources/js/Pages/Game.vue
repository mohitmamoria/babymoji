<script setup>
import emojis from "@/renderable-emojis.json";
import { Head } from "@inertiajs/vue3";
import { onMounted, ref } from "vue";

function renderEmoji(emoji) {
    const codes = emoji.code.map((code) => "0x" + code);
    return String.fromCodePoint(...codes);
}

function getRandomEmoji() {
    const index = Math.floor(Math.random() * emojis.length);

    return renderEmoji(emojis[index]);
}

let emoji = ref(getRandomEmoji());

onMounted(() => {
    addEventListener("keydown", (event) => {
        emoji.value = getRandomEmoji();
    });
});
</script>

<template>
    <Head title="👼 Babymoji" />

    <div class="h-dvh flex items-center justify-center">
        <p class="text-[14rem]">{{ emoji }}</p>
    </div>
</template>

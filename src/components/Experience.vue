<template>
    <div class="experience">
        <div class="player" ref="domPlayer"></div>
    </div>
</template>

<script>
export const Languages = {
    AU: 'au',
    CA: 'ca',
    CH: 'ch',
    DE: 'de',
    DK: 'dk',
    ES: 'es',
    FR: 'fr',
    IT: 'it',
    NL: 'nl',
    NO: 'no',
    SE: 'se',
    SG: 'sg',
    UK: 'uk',
    DEFAULT: 'us',
};
</script>

<script setup>
import {onMounted, reactive, ref} from "vue";

let ruffle = null;
let player = null;
const domPlayer = ref(null);

const props = defineProps({
    language: {
        type: String,
        required: true,
        default: Languages.DEFAULT,
    }
});

onMounted(() => {
    console.log("[Experience] Loading");

    window.RufflePlayer.config = {
        "autoplay": "on",
        "backgroundColor": "#000000",
        "logLevel": "warn",
        "warnOnUnsupportedContent": true,
        "quality": "high",
        "base": "/experience",
        "contextMenu": "off",
        "showSwfDownload": false,
        "splashScreen": false,
        "allowScriptAccess": true,
    };
    ruffle = window.RufflePlayer.newest();
    player = ruffle.createPlayer();
    player.style.width = "650px";
    player.style.height = "450px";
    domPlayer.value.appendChild(player);
    player.load("/experience/main.swf?language=" + props.language);

    console.log("[Experience] Done");
});
</script>

<style scoped>
.experience {
    background: #000;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0px 0px 50px 50px #000;
}
</style>
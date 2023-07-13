<template>
    <div class="intro-box">
        <div class="box">
            <div class="inner">
                <img src="/group.png" alt="DJ_Shadow, Chaplin, Faith and Cherry-Bomb" />
                <div class="header">
                    <strong>Habbo Experience</strong>
                    <p>The Habbo Experience was an interactive tutorial for Habbo Hotel. Made in 2005, it showcased the social interactions possible in the popular virtual space. Please select a Hotel to continue.</p>
                </div>
                <div class="buttons">
                    <HabboButton
                        v-for="language in Object.values(Languages)"
                        :key="language"
                        @click="emit('change', language)"
                    >
                        {{ languageToHotel(language) }}
                    </HabboButton>
                </div>
                <p>This project uses <a href="https://github.com/ruffle-rs/ruffle" target="_blank">Ruffle</a> to make this experience usable in modern browsers without the need of Flash Player.</p>
            </div>
        </div>
        <footer>
            <strong>Made with &fnof; by Laura Sofia.</strong>
            <span>This website is for preservational purposes only.<br />&copy; 2005 Sulake Oy. HABBO is a registered trademark of Sulake Oy.</span>
        </footer>
    </div>
</template>

<script setup>
import { Languages } from "./Experience.vue";
import HabboButton from "./HabboButton.vue";

const emit = defineEmits(['change']);

const languageToHotel = (language) => {
    let text = "Default (English)";

    switch(language) {
        case "au":
            text = "Australia";
            break;
        case "ca":
            text = "Canada";
            break;
        case "ch":
            text = "Austria";
            break;
        case "de":
            text = "Germany";
            break;
        case "dk":
            text = "Denmark";
            break;
        case "es":
            text = "Spain";
            break;
        case "fr":
            text = "France";
            break;
        case "it":
            text = "Italy";
            break;
        case "nl":
            text = "Netherlands";
            break;
        case "no":
            text = "Norway";
            break;
        case "se":
            text = "Sweden";
            break;
        case "sg":
            text = "Singapore";
            break;
        case "uk":
            text = "United Kingdom";
            break;
    }

    return text;
};
</script>

<style scoped>
.intro-box {
    width: 90%;
    max-width: 500px;
    display: flex;
    flex-direction: column;
    gap: 25px;
}
.intro-box .box {
    background: #6794a7;
    padding: 14px;
    border: 2px solid #000;
    border-radius: 15px;
    box-shadow: inset 1px 1px 0 #79aec4;
}
.intro-box .box .inner {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: #efefef;
    padding: 20px;
    border-radius: 7px;
    border: 1px solid #000;
    box-shadow: 1px 1px 0 rgba(0,0,0,0.2);
}
.intro-box .box .header, .intro-box .box p {
    text-align: center;
    padding: 0;
}
.intro-box .box .buttons {
    padding: 10px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
}
.intro-box footer {
    color: rgba(255,255,255,0.3);
    text-align: center;
    display: flex;
    flex-direction: column;
    gap: 5px;
}
</style>
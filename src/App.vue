<template>
    <template v-if="selectedLanguage !== null">
        <HabboButton
            @click="() => { selectLanguage(null); }"
            class="button-back"
        >
            Back
        </HabboButton>
        <Experience
            :language="selectedLanguage"
            :key="selectLanguage"
        />
    </template>
    <IntroBox v-else @change="(language) => { selectLanguage(language); }" />
</template>

<script setup>
import {onMounted, ref} from "vue";

import Experience from "./components/Experience.vue";
import IntroBox from "./components/IntroBox.vue";
import HabboButton from "./components/HabboButton.vue";

const selectedLanguage = ref(null);

const selectLanguage = (language) => {
    history.pushState(null, null, language !== null ? '#experience-' + language : '');
    selectedLanguage.value = language;
};

onMounted(() => {
    // This is a bit cumbersome, but I don't want to import vue-router just for this
    window.addEventListener('hashchange', (e) => {
        // Experience -> Default
        if(selectedLanguage.value !== null) {
            selectedLanguage.value = null;
            history.pushState(null, null, '');
        }

        // Default -> Experience
        if(e.newURL.includes("#experience")) {
            selectedLanguage.value = e.newURL.split("#experience-")[1] ?? 'default';
        }
    });
});
</script>

<style scoped>
.button-back {
    position: absolute;
    z-index: 100;
    top: 10px;
    left: 10px;
    padding: 7px 20px;
}
</style>

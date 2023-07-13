<template>
    <button v-bind="$attrs"><slot /></button>
</template>

<style scoped>
button {
    position: relative;
    z-index: 10;
    appearance: none;
    cursor: pointer;
    font-family: "Volter", monospace;
    font-weight: bold;
    font-size: 1rem;
    padding: 5px 10px;
    border-radius: 3px;
    background: #eeeeee;
    box-shadow: inset -1px -1px 0 rgba(0,0,0,0.2);
    border: 1px solid #000;
}
button:before {
    content: " ";
    position: absolute;
    z-index: -1;
    top: -4px;
    bottom: -4px;
    left: -4px;
    right: -4px;
    border: 2px solid transparent;
    border-radius: 4px;
}
button:hover {
    background: #dedede;
}
button:active:before {
    border-color: #000;
}
</style>
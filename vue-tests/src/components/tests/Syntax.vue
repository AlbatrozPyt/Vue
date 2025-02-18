<script setup>
import { ref } from 'vue';

const helloWorld = '<p style="color: red">Hello World</p>';

const isTrue = ref(false);
</script>

<template>
    <div class="align-content">
        <p>Texto simples: {{ helloWorld }}</p>
        <p>Html puro: <span v-html="helloWorld"></span></p>

        <button @click="isTrue = !isTrue">is {{ isTrue }}</button>
    </div>
</template>

<style scoped>
.align-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
</style>

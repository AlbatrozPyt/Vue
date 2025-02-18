<script setup>
import { computed, ref } from 'vue';

let bookName = ref('');
const books = ref(['A Metamorfose']);

const readerLevel = computed(() => {
    return books.value.length < 2 ? 'básico' : books.value.length < 3 ? 'médio' : 'avançado';
});

function AddBook() {
    books.value.push(bookName.value);
    bookName.value = '';
}
</script>

<template>
    <p>Nivel de leitura: {{ readerLevel }}</p> 


    <input type="text" @input="e => bookName = e.target.value">
    <button @click="AddBook()">Adicionar</button>

    <ul v-for="book in books">
        <li>{{ book }}</li>
    </ul>
</template>

<style scoped>
ul {
    display: grid
}
</style>
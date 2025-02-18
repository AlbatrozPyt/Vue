<script setup>
import { ref } from 'vue';
import ContainerMain from './ContainerMain.vue'

const search = ref('');
</script>

<template>
    <ContainerMain>
        <section class="search">
            <slot name="search" />
        </section>

        <section class="cards">
            <h2>Aqui fica os dados dos pokemons</h2>
            <slot name="cards" />
        </section>
    </ContainerMain>
</template>

<style scoped>
section {
    display: flex;
    justify-content: center;
    margin: 5% 0;
    width: 100%;
}

.cards {
    flex-direction: column;
    align-items: center;
}
</style>
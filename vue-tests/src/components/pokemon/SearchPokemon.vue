<script setup>
import { ref, watch, watchEffect } from 'vue';

const search = ref('');

watch(search, async () => {
    const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${search.value}`);
    console.log(res);
});

</script>

<template>
    <form>
        <input type="text" @input="e => search = e.target.value">

        <button type="button">
            <img src="../icons/search.svg" alt="lupa">
        </button>
    </form>
</template>

<style scoped>
form {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 30px;
    background: #fff;
    box-shadow: 5px 5px 10px #d9d9d9, -5px -5px 10px #ffffff;
    border-radius: 5px;
    width: 50%;
    height: 80px;
}

form input {
    background: #ffffff;
    box-shadow: inset 5px 5px 10px #d9d9d9, inset -5px -5px 10px #ffffff;
    padding: 3px 0 3px 25px;
    width: 70%;
    height: 35%;
    border: none;
    outline: none;
}

form button { 
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #0b239d;
    /* box-shadow: 5px 5px 10px #d9d9d9, -5px -5px 10px #ffffff; */
    padding: 10px;
    border-radius: 5px;
    width: 10%;
    border: none;
    outline: none;
}

form button img {
    width: 30px;
}
</style>
<script setup>
import { ref, watch } from 'vue';
import Layout from './components/layouts/Layout.vue';

const search = ref('');
const pokemon = ref(null);

watch(search, async () => {
  const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${search.value}`);

  if (res.status === 200) {
    pokemon.value = await res.json();
    return;
  }

  pokemon.value = null;
});
</script>

<template>
  <Layout>
    <template #search>
      <form>
        <input type="text" @input="e => search = e.target.value">

        <button type="button">
          <img src="./components/icons/search.svg" alt="lupa">
        </button>
      </form>
    </template>

    <template #cards>
      <div class="card" v-if="pokemon !== null">
        <img :src="pokemon.sprites.front_default" alt="">
        {{ pokemon.name }}
      </div>
    </template>
  </Layout>
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

.card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  width: 300px;
  height: 350px;
  border: 2px solid;
  border-radius: 10px;
}

.card>img {
  object-fit: contain;
}
</style>

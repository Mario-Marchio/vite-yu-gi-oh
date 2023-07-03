<script>
import { store } from '../components/store.js'
export default {
    data() {
        return { store }
    }
};
</script>

<template>
    <div class="container">
        <div class="row row-cols-5 justify-content-center">
            <div v-for="pokemon in store.pokemons" :key="pokemon.id">
                <img :src="pokemon.imageUrl" :alt="pokemon.name" class="img-fluid">
                <h1>{{ pokemon.number }}</h1>
                <h1>{{ pokemon.name }}</h1>
                <h1>{{ pokemon.type1 }}</h1>

            </div>

        </div>
    </div>
</template>


<style></style>
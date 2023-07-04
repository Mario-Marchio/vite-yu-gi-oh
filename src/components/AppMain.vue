<script>

import axios from 'axios';
import SearchOption from './SearchOption.vue'
const endpoint = 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons';
import { store } from './store.js'

export default {
    components: { SearchOption },
    data() {

        return {
            filteredPokemons: []

        }
    },
    created() {
        // qua prendo i primi 10 pokemon 
        axios.get(endpoint)
            .then(res => {
                store.pokemons = res.data.docs;
                this.filteredPokemons = store.pokemons;
            })
            .catch(error => {
                console.log(error);
            });
    },
    methods: {
        // qua prendo i primi 10 pokemon del tipo che ho selezionato e portato qua grazie a emit 
        filterPokemonsByType(selectedType) {
            const apiUrl = selectedType ? `${endpoint}?eq[type1]=${selectedType}` : endpoint;

            axios.get(apiUrl)
                .then(res => {
                    this.filteredPokemons = res.data.docs;
                })
                .catch(error => {
                    console.log(error);
                });
        },
    },

}

</script>

<template>
    <div class="container">
        <SearchOption @type-selected="filterPokemonsByType" />
        <div class="row row-cols-5 justify-content-center">
            <div v-for="pokemon in filteredPokemons" :key="pokemon.id">
                <img :src="pokemon.imageUrl" :alt="pokemon.name" class="img-fluid">
                <h1>{{ pokemon.number }}</h1>
                <h1>{{ pokemon.name }}</h1>
                <h1>{{ pokemon.type1 }}</h1>

            </div>

        </div>
    </div>
</template>


<style></style>
<script>
export default {
    data() {

        return {
            options: [
                "Bug",
                "Dark",
                "Dragon",
                "Electric",
                "Fairy",
                "Fighting",
                "Fire",
                "Flying",
                "Ghost",
                "Grass",
                "Ground",
                "Ice",
                "Normal",
                "Poison",
                "Psychic",
                "Rock",
                "Steel",
                "Water"
            ],
            selectedType: ""
        }

    },
    methods: {
        filterPokemons() {
            this.$emit('type-selected', this.selectedType);
        },
    },

}

</script>


<template>
    <div class="search-option">
        <select v-model="selectedType" @change="filterPokemons">
            <option value="">Seleziona un tipo</option>
            <option v-for="option in options" :value="option" :key="option">{{ option }}</option>
        </select>
    </div>
</template>



<style></style>
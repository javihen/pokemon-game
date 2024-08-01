<template>
<h2>Quien es este pokemon?</h2>
        <!-- TODO: Componente Picture -->
    <PokemonPicture :pokemonId="300" :showPokemon="true"/>
        <!-- TODO: Componente Opciones -->
    <PokemonOption :pokemons="pokemonArr"/>
</template>
<script>

import  PokemonPicture  from "@/components/PokemonPicture.vue";
import PokemonOption from "../components/PokemonOption.vue";
import getPokemonOptions from "@/helpers/getPokemonOptions";

//console.log(getPokemonOptions())

export default {
    components: { PokemonPicture, PokemonOption },
    data() {
        return {
            pokemonArr:[]
        }
    },
    methods: {
        /**Revisar el metodo de async await en javascript */
       async mixPokemonArray() {
            this.pokemonArr = await getPokemonOptions()
            console.log(this.pokemonArr)
    }
    },
    mounted() {
    this.mixPokemonArray()
   }
    
}
</script>
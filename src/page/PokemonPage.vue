<template>
    <h1 v-if="!pokemon">Espere por favor ...</h1>
    <div v-else>
        <h2>Quien es este pokemon?</h2>
        <!-- TODO: Componente Picture -->
        <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
        <!-- TODO: Componente Opciones -->
        <PokemonOption :pokemons="pokemonArr"/>
    </div>
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
            pokemonArr: [],
            pokemon: null,
            showPokemon: false
        }
    },
    methods: {
        /**Revisar el metodo de async await en javascript */
       async mixPokemonArray() {
            this.pokemonArr = await getPokemonOptions()
            const rndInt = Math.floor(Math.random() * 4)
            this.pokemon = this.pokemonArr[rndInt]
            console.log(this.pokemonArr)
            console.log(rndInt)
    }
    },
    mounted() {
    this.mixPokemonArray()
   }
    
}
</script>
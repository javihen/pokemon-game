<template>
    <h1 v-if="!pokemon">Espere por favor ...</h1>
    <div v-else>
        <h2>Quien es este pokemon?</h2>
        <!-- TODO: Componente Picture -->
        <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
        <!-- TODO: Componente Opciones -->
        <PokemonOption :pokemons="pokemonArr" @selection="checkAnswer($event)"/>
    </div>
    <div v-if="showAnswer">
        <h2>{{ message }}</h2>
        <button @click="newGame">Nuevo Juego</button>
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
            showPokemon: false,
            message: null,
            showAnswer:false
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
        },
        checkAnswer(pokemonId) {
            this.showAnswer= true
            this.showPokemon = true;
            console.log('Pokemon Page llamado', pokemonId)
            if (pokemonId === this.pokemon.id) {
                this.message = `Correcto, ${ this.pokemon.name}`
            } else {
                this.message = `Oops, era ${ this.pokemon.name}`
                
            }
        },
        newGame() {
            this.showPokemon = false
            this.showAnswer = false
            this.pokemonArr = []
            this.pokemon = null
            this.mixPokemonArray()
    }
    },
    mounted() {
    this.mixPokemonArray()
   }
    
}
</script>
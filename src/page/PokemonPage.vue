<template>
<h2>Quien es este pokemon?</h2>
        <!-- TODO: Componente Picture -->
    <PokemonPicture :pokemonId="10" :showPokemon="true"/>
        <!-- TODO: Componente Opciones -->
    <PokemonOption />
</template>
<script>

import  PokemonPicture  from "@/components/PokemonPicture.vue";
import PokemonOption from "../components/PokemonOption.vue";
import getPokemonOptions from "@/helpers/getPokemonOptions";

console.log(getPokemonOptions())

export default {
    components: { PokemonPicture, PokemonOption },
    
   
    
}
</script>
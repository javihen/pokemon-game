<template>
    <div class="pokemon-container">
        <img v-bind:src="imgSrc" class="hidden-pokemon" alt="">
        <img v-if="showPokemon" v-bind:src="imgSrc" class="fade-in" alt="">
    </div>
</template>

<script>
export default {
    /**Capturamos el parametro pokemonId que se envia fuera del componente */
    props: {
        pokemonId: {
            type: Number,   /**Debe ser de tipo numerico y de forma forzosa debe haber un dato */
            required:true
        },
        showPokemon: {
            type: Boolean,
            required: true,
            default:false
        }
    },
    computed: {
        imgSrc() {
            /**Retornamos la imagen que se busca con el parametro pokemonId */
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${ this.pokemonId }.svg`;
        }
    }

}
</script>

<style scoped>
.pokemon-container {
    height: 200px;
}
img {
    height: 200px;
    position: absolute;
    right: 32%;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}
.hidden-pokemon {
    filter: brightness(0);
}


</style>
<template>
<div class="options-container">
    <ul>
        <li>1</li>
    </ul>
</div>
</template>

<script scoped>
export default {
    props: {
        pokemons: {
            type: Array,
            required:true
        }
    }

}
</script>

<style>
/* Pokemon Options */
ul {
    list-style-type: none;
}
li {
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.2);
    cursor: pointer;
    margin-bottom: 10px;
    width: 250px;
/*     He colocado este atributo de forma extra */    
padding: 10px 10px;
}

li:hover {
    background-color: rgba(0, 0, 0, 0.05);
}

.options-container {
    display: flex;
    justify-content: center;
}
</style>
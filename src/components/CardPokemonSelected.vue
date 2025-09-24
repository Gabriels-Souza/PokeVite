<script setup>
const pokemon = defineProps(["name", "xp", "height", "urlBasePng", "loading"]);


</script>


<template>
    <div 
    class="card CardPokemonSelected"
    :class=" loading ? '' : 'animate__animated animate__flipInY'"
    >
        <img 
        v-if="pokemon.name"
        :src="urlBasePng" 
        class="card-img-top pt-2" 
        :alt="pokemon.name">

        <img 
        v-else
        src="../assets/egg_pokemon.svg" 
        class="card-img-top pt-2" 
        alt="???">

        <div class="card-body">
            <h5 class="card-title text-center">{{pokemon.name || '???'}}</h5>
            <hr>
            <div class="row text-center">
                <section class="col">
                    <strong>XP:</strong>
                    <span v-if="pokemon.xp">{{" " + pokemon.xp}}</span>
                    <span v-else> ???</span>
                </section>
                <section class="col">
                    <strong>Altura:</strong>
                    <span v-if="pokemon.height">{{" " + pokemon.height}}</span>
                    <span v-else> ???</span>
                </section>
            </div>
        </div>
    </div>  
</template>


<style scoped>
.CardPokemonSelected{
    border: none;
    box-shadow: none;
    margin-bottom: 1rem;
    height: 75vh;
    max-height: 75vh;
    overflow-y: auto;
    background: linear-gradient(
    90deg,
    #E4B9DD 0%,
    #C5E7D2 50%,
    #FDF8C1 100%
    );

    scrollbar-width: auto;
    scrollbar-color: rgb(83, 83, 83) transparent;

}

.CardPokemonSelected img{
    max-height: 340px;
    margin: 0 auto;
    display: block;
    width: auto;
    object-fit: contain;
}


</style>
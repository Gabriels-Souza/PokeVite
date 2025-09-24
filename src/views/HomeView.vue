<script setup>
import { onMounted, reactive, ref, computed } from 'vue';
import ListPokemons from '../components/ListPokemons.vue';
import CardPokemonSelected from '../components/CardPokemonSelected.vue';

let urlBasePng = ref("https://www.pokemon.com/static-assets/content-assets/cms2/img/pokedex/full/");

let pokemons = reactive(ref());

let searchPokemonField = ref("");

let pokemonSelected = reactive(ref());

let loading = ref(false);

onMounted(() => {
    fetch("https://pokeapi.co/api/v2/pokemon?limit=649&offset=0")
    .then(res => res.json())
    .then(res => pokemons.value = res.results);

});

const pokemonsFiltered = computed(() => {
    if(pokemons.value && searchPokemonField.value == ""){
        return pokemons.value
    }
    else if(pokemons.value && searchPokemonField.value){
        return pokemons.value.filter(pokemon => 
            pokemon.name.toLowerCase().includes(searchPokemonField.value)
        )
    }
});


const selectPokemon = async (pokemon) =>{
    loading.value = true;
    await fetch(pokemon.url)
    .then(res => res.json())
    .then(res => pokemonSelected.value = res)
    .catch(err => alert(err))
    .finally(() => loading.value = false)

    console.log(pokemonSelected.value);

};


</script>


<template>
    <main>
        <div class="container">
            <div class="row mt-4">

                <div class="col-sm-12 col-md-6">
                    
                    <CardPokemonSelected 
                    :name="pokemonSelected?.name"
                    :xp="pokemonSelected?.base_experience"
                    :height="pokemonSelected?.height"
                    :urlBasePng = "urlBasePng + Number(pokemonSelected?.id).toString().padStart(3, '0') + '.png'"
                    :loading="loading"
                    />
                    <br>

                </div>


                <div class="col-sm-12 col-md-6">
                    <div class="card card-list">
                        <div class="card-body row">

                            <div class="mb-3">
                                <label 
                                hidden for="searchPokemonField" 
                                class="form-label">
                                Encontre seu Pokémon
                                </label>

                                <input 
                                type="text" 
                                class="form-control input-personalizado" 
                                id="searchPokemonField" 
                                placeholder="Pesquisar..."
                                v-model="searchPokemonField">
                            </div>

                            <ListPokemons
                            v-for="pokemon in pokemonsFiltered" 
                            :key="pokemon.name" 
                            :name = "pokemon.name"
                            :urlBasePng = "urlBasePng + Number((pokemon.url.split('/')[6])).toString().padStart(3, '0') + '.png'"
                            @click="selectPokemon(pokemon)"
                            />
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </main>
</template>

<style scoped>
.card-list{
    background-color: rgb(107, 107, 107);
    max-height: 75vh;
    margin-bottom: 1rem;
    overflow-y: scroll;
    overflow-x: hidden;

    scrollbar-width: auto;
    scrollbar-color: rgb(83, 83, 83) transparent;
}

.input-personalizado{
    border: none;
    box-shadow: none;
    background-color: rgb(83, 83, 83);
    color: white;
}

input::placeholder{
    color: white;
    opacity: 1;
    
}



.card-list::-webkit-scrollbar {
  width: 12px;
  height: 12px; 
}


</style>

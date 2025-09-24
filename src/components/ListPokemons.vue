<script setup>
const pokemon = defineProps(["name", "urlBasePng"]);
</script>


<template>
    <div class="col-4">
        <div class="card p-2 mb-4 cardListPokemon">
            <p class="text-center">{{ pokemon.name }}</p>
            <img 
            :src="urlBasePng" class="card-img-top" 
            alt="..."
            />
        </div>
    </div>
</template>


<style scoped>

.cardListPokemon {
    border: none;
    box-shadow: none;
    background: linear-gradient(
        90deg,
        #AECFDC 0%,
        #C5E7D2 50%,
        #F7F2BE 100%
    );
    cursor: pointer;
}


.cardListPokemon:hover {
  background: linear-gradient(
    90deg,
    #71A7BF 0%,
    #96D0AF 50%,
    #EFE373 100%
  );
  cursor: pointer;
}


.cardListPokemon:hover img {
  padding: .1rem;
}



</style>
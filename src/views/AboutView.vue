<script setup>

</script>


<template>
    <div class="container tipo1 mt-4">
        <div class="card text-light">
            <h1 class="text-center mt-2">
                PokeVite
            </h1>
        </div>
    </div>
    
    <br>

    <div class="container tipo2">
        <div class="card text-light animate__animated animate__slideInLeft animate__fast">
            <h2 class="text-center mt-3">
                Sobre o Projeto
            </h2>

            <br>

            <div class="p-3">
                <h3> Objetivo </h3>
                <p>
                    Esse projeto trata-se de um estudo didático sobre o uso das frameworks Vue.js e Vite, 
                    além dos conhecimentos gerais de frontend (HTML, CSS e Javascript), com a personalização
                    fornecida pelo Bootstrap.
                </p>
                <!---->
                <br>
                <!---->
                <h3> GitHub </h3>
                <a href="" target="_blank" class="btn buttonCustom fw-semibold"> Repositório PokeVite </a>
                <!---->
                <br>
                <br>
                <br>
                <!---->
                <h3> Curso Base </h3>
                <p>
                    Esse projeto foi baseado no ensino apresentado no curso "Vue JS 3, Vuetify, Pinia, Vue Router e mais".
                </p>
                <a href="https://www.udemy.com/course/curso-front-end-developer-vue" target="_blank" class="btn buttonCustom fw-semibold"> Acesse o curso na Udemy! </a>
                <!---->
                <br>
                <br>
                <br>
                <!---->
                <h3> Minhas Redes </h3>
                <p>
                    ???
                </p>

            </div>

        </div>

    </div>
</template>


<style scoped>
@media (min-width: 1024px) {
    .about{
        display: flex;
        align-items: center;
    }
}

.card{
    background-color: rgb(59, 59, 59);
    border: none;
    box-shadow: none;
}

.tipo1{
    max-height: 10vh;
}

.tipo2{
    min-height: 100vh;
    margin-bottom: 1rem;
}

.buttonCustom{
    background-color: rgb(184, 1, 184);
    color: white;
    cursor: pointer;
    
}

.buttonCustom:hover{
    background-color: rgb(136, 0, 136);
    color: white;
    cursor: pointer;
}


</style>
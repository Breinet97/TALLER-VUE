<script setup>

import Cuadrado from './cuadrado.vue';

// si puedo saber el id de cada uno, puedo modificarlo para que me den su posicion 
// for (let i = 1; i <= 81; i++) {
//     console.log('ID del cuadrado: '+ i);
//     // identifica la posicion de mi jugador 
//     if(i===positionPlayerOne){
//         console.log("Jugador Uno");
//     }else if (i===positionPlayerTwo){
//         console.log("Jugador Dos");
//     }
// }
</script>

<template>
    <main class="main-tablero">
        <section class="tablero" id="tablero">
            <cuadrado v-for="i in 81" :key="i" :id="i"/>
        </section>
    </main>
</template>

<style scoped>
.tablero {
    width: 100%;
    display: grid;
    gap: 8px;
    grid-template-columns: repeat(9, 100px);
    justify-content: center;
}

</style>
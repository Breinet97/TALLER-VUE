<script setup>

import Cuadrado from './cuadrado.vue';
import {ref}  from 'vue';

// posicion inicial de los dos jugadores 
const positionPlayerOne= ref(5);

// REACTIVDAD: usamos el ref para hacer reactivas estas constantes y hace poder tenerlas lista para cualquiier cambio durante su ejecucion.
// Esto me ayudara a poder cambiar a mi jugador de posicion si afectar a estas constantes directamente

const positionPlayerTwo= ref(77);

// los jugadores debn poder moverse por el tablero asi que debe aqui ir la funcion de movimiento 

// Función para mover jugadores (REVISAR)
const movePlayer = (player, newPosition) => {
  if (player === 1) {
    positionPlayerOne.value = newPosition;
  } else if (player === 2) {
    positionPlayerTwo.value = newPosition;
  }
};




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
            <cuadrado v-for="i in 81" :key="i" :id="i"
            :positionPlayerOne="positionPlayerOne"
            :positionPlayerTwo="positionPlayerTwo"
            @movePlayer="movePlayer"
            />
            <!-- enviamos la posicion inicial a cuadrado  -->
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
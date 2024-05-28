<script setup>

import Cuadrado from './cuadrado.vue';
import { ref } from 'vue';

// posicion inicial de los dos jugadores 
const positionPlayerOne = ref(5);

// REACTIVDAD: usamos el ref para hacer reactivas estas constantes y hace poder tenerlas lista para cualquiier cambio durante su ejecucion.
// Esto me ayudara a poder cambiar a mi jugador de posicion si afectar a estas constantes directamente

const positionPlayerTwo = ref(77);

// id del cuadrado cliqueado 
let clickPlayer = ref(0);

// jugadores 
const playerOne = 1;
const playerTwo = 2;

// estado del jugador, empieza
let activePlayer = playerOne;

// condiciones de movimiento para que sea solo una casilla
// let nextCuadrado = id + 9;
// let leftCuadrado = id + 1;
// let rightCuadrado = id - 1;

// Función para saber a donde cliqueo mi jugador
const clickMovePlayer = (id) => {

  let nextCuadrado = positionPlayerOne.value + 9;
  let leftCuadrado = positionPlayerOne.value - 1;
  let rightCuadrado = positionPlayerOne.value + 1;
  let backCuadrado = positionPlayerOne.value - 9;

  // console.log("ID QUE TENGO"+id);
  // console.log("CASILLA DONDE SE HIZO CLICK"+clickPlayer);

  console.log("CASILLA DONDE DEBERIA MOVERCE"+nextCuadrado);

  if (id === nextCuadrado) {
    movePlayer(activePlayer, id)

  }else if(id === leftCuadrado){
    movePlayer(activePlayer, id)

  }else if(id === rightCuadrado){
    movePlayer(activePlayer, id)
  }else if(id === backCuadrado){
    movePlayer(activePlayer, id)
  }
  else{
    alert("Ten en cuenta que solo puedes moverte un casilla menos en las casillas que se encuentren en diagonal");
  }
};

// Función para mover jugadores (REVISAR)
const movePlayer = (player, newPosition) => {

  if ((newPosition === positionPlayerOne.value) || (newPosition === positionPlayerTwo.value)) {
    alert("No te puedes mover, la casilla ya esta ocupada. Intenta con otra")
  } else {
    // movimiento de los dos jugadores  
    if (player === playerOne) {
      positionPlayerOne.value = newPosition;
      // cambia de jugador 
      activePlayer = 2;
    } else if (player === playerTwo) {
      positionPlayerTwo.value = newPosition;
      // cambia de jugador 
      activePlayer = 1;
    }
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
      <cuadrado v-for="i in 81" :key="i" :id="i" :positionPlayerOne="positionPlayerOne"
        :positionPlayerTwo="positionPlayerTwo" @click="clickMovePlayer(i)" />
      <!-- @click = "clickMovePlayer(i)" -->
      <!-- :clickPlayer = "clickPlayer"
            @movePlayer="movePlayer" -->
      <!-- @movePlayer="movePlayer" -->
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
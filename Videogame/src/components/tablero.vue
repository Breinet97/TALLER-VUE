<script setup>

import Cuadrado from './cuadrado.vue';
import { ref } from 'vue';

// posicion inicial de los dos jugadores 
const positionPlayerOne = ref(5);

// REACTIVDAD: usamos el ref para hacer reactivas estas constantes y hace poder tenerlas lista para cualquiier cambio durante su ejecucion.
// Esto me ayudara a poder cambiar a mi jugador de posicion si afectar a estas constantes directamente

const positionPlayerTwo = ref(77);

// jugadores 
const playerOne = 1;
const playerTwo = 2;

// estado del jugador, empieza
let activePlayer = playerOne;

// mueve o bloquea  (move) or (block) con los botones
const actionMode = ref('move'); // 'move' o 'block'

// Función para saber a donde cliqueo mi jugador
const clickMovePlayer = (id) => {

  if (actionMode.value === 'block' && (id === positionPlayerOne.value || id === positionPlayerTwo.value)) {
    // Si el jugador está en modo de bloqueo y hace clic en su propia posición, bloquea la casilla
    blockSquare(id);



  } else {
    if (activePlayer === playerOne) {

      let nextCuadrado = positionPlayerOne.value + 9;
      let leftCuadrado = positionPlayerOne.value - 1;
      let rightCuadrado = positionPlayerOne.value + 1;
      let backCuadrado = positionPlayerOne.value - 9;

      if (id === nextCuadrado || id === leftCuadrado || id === rightCuadrado || id === backCuadrado) {
        movePlayer(activePlayer, id)
      }
      else {
        alert("Ten en cuenta que solo puedes moverte un casilla menos en las casillas que se encuentren en diagonal");
      }
    } else if (activePlayer === playerTwo) {

      let nextCuadrado = positionPlayerTwo.value + 9;
      let leftCuadrado = positionPlayerTwo.value - 1;
      let rightCuadrado = positionPlayerTwo.value + 1;
      let backCuadrado = positionPlayerTwo.value - 9;

      if (id === nextCuadrado || id === leftCuadrado || id === rightCuadrado || id === backCuadrado) {
        movePlayer(activePlayer, id)
      }
      else {
        alert("Ten en cuenta que solo puedes moverte un casilla menos en las casillas que se encuentren en diagonal");
      }
    }
  }
};

// Función para cambiar el modo de acción
const setActionMode = (mode) => {
  actionMode.value = mode;
};

// Función para verificar si un jugador ha ganado
const checkWin = (player, position) => {
  if (player === playerOne && position >= 72 && position <= 81) {
    alert("¡PlayerOne gana!");
  } else if (player === playerTwo && position >= 1 && position <= 9) {
    alert("¡PlayerTwo gana!");
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
      checkWin(player,newPosition);
      // cambia de jugador 
      activePlayer = 2;
    } else if (player === playerTwo) {
      positionPlayerTwo.value = newPosition;
      checkWin(player,newPosition);
      // cambia de jugador 
      activePlayer = 1;
    }
  }
};

// Función para bloquear casillas 
const blockSquare = (id) => {
  if (id === positionPlayerOne.value || id === positionPlayerTwo.value) {
    alert("No puedes bloquear esta casilla.");
  } else {
    // Agrega la casilla bloqueada al arreglo de casillas bloqueadas
    // Aquí deberías implementar tu lógica para manejar las casillas bloqueadas
    // Por ejemplo, podrías mantener un arreglo de las casillas bloqueadas y usarlo en tu lógica de movimiento para evitar que los jugadores se muevan a esas casillas
    alert("Casilla bloqueada:", id);
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
    </section>
    <button class="main-button" @click="setActionMode('block')">Bloquear</button>
  </main>
</template>

<style scoped>
.tablero {
  position: relative;
  width: 100%;
  display: grid;
  gap: 8px;
  grid-template-columns: repeat(9, 100px);
  justify-content: center;
}
.main-button{
  position: absolute;
  background-color: red;
  border: black 2px solid ;
  color: white;
  font-size: 1.3rem;
  border-radius: 5px;
  padding: 1.5rem;
  top: 10%;
  left: 10%;
}
</style>
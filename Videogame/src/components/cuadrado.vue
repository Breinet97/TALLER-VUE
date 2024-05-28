<script setup>

import Player from './player.vue';


import { defineProps, defineEmits } from 'vue';

// lo que voy a hacer es traerme a i para poder cambiar el valor de esos cuadrados con un if 

const props = defineProps({
    // aqui estaran las id que necesito para modificar el color 
    id: {
        type: Number,
        // lo que required no entiendo pa que xd 
        required: true
    },
    // posicion inicial de los jugadores para que sean renderizados
    // estos vienen desde tablero 
    positionPlayerOne: {
        type: Number,
        required: true
    },
    positionPlayerTwo: {
        type: Number,
        required: true
    },
    // clickPlayer:{
    //     type:Number,
    //     required: true
    // }
});


// REVISAR FUNCION MOVIMIENTO 

// evento de movimiento 
const eventMove = defineEmits(['movePlayer']);

// manejar el movimiento del jugador 
// obtiene como parametro al jugador y en base a eso creamos una nueva posicion para nuestro cuadrado
const handleMove = (player) => {


    // let newPosition = props.id + 1; 
    let newPositionFinal = props.id + 1;
    
    // let newPositionFinal;

    // let positionPlayer = props.id;

    // console.log("posicion jugador"+positionPlayer);
    // console.log("Props click"+props.clickPlayer);


    // let nextCuadrado = props.id + 9;
    // let leftCuadrado = props.id + 1;
    // let rightCuadrado = props.id -1;


    // debemos comparar si el cuadrado cliqueado es el que esta adelante en ese caso si me cambia la posicion 

    // if (props.clickPlayer === "ojito") {
    //     newPosition = props.clickPlayer; // Mover hacia adelante (9 casillas)
    // } else if (props.direction === 'izquierda') {
    //     newPosition = props.clickPlayer; // Mover hacia la izquierda (1 casilla)
    // } else if (props.direction === 'derecha') {
    //     newPosition = props.clickPlayer; // Mover hacia la derecha (1 casilla)
    // } else {
    //     // Dirección no válida
    //     console.log('Dirección no válida');
    //     return;
    // }
    // eventMove es una funcion para generar el evento de movimiento que llama a movePlayer que esta en tablero para lograr generar la nueva posicion 
    // esta funciona llamando a la funcion, luego la posicion actual del jugador y por ultimo dandole la nueva posicion
    eventMove('movePlayer', player, newPositionFinal);
};

</script>
<template>
    <!-- aplica el estilo solo si  -->

    <!-- REVISAR FUNCION DE MOVIMIENTO  -->
    <section class="cuadrado"
        :class="{ 'cuadrado': true, 'cuadrado-one': id === positionPlayerOne, 'cuadrado-two': id === positionPlayerTwo }"
        @click="id === positionPlayerOne ? handleMove(1) : id === positionPlayerTwo ? handleMove(2) : null">

        <!-- tener en cuenta que para traer valores de otro componente estos tienen que llamarse igual al que puse en el v-bind :playerId por ejemplo debe coincidir con el prop  -->

        <!-- solo se renderiza si  -->
        <Player :playerId=1 v-if="id === positionPlayerOne" />
        <!-- id que identifica cada una para luego estilizarlo  -->
        <Player :playerId=2 v-if="id === positionPlayerTwo" />
    </section>
</template>

<style scoped>
.cuadrado {
    /* 
    para reconocer el turno dle jugador lo que haremos es un truco:
    sabremos que pulsan teniendo simbolos y encima la imagen, asi sabre el turno y ganador 
    */
    /* position: relative; */
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 5px solid black;
    background-color: rgba(0, 0, 0, 0.699);
    font-size: 18px;

}

.cuadrado:hover {
    background-color: aqua;
    transform: translate(10px, -10px);
}

.cuadrado:active {
    background-color: red;
}

.cuadrado-one {
    background-color: orange;
}

.cuadrado-two {
    background-color: blueviolet;
}
</style>
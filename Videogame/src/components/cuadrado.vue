<script setup>

import Player from './player.vue';

import { defineProps } from 'vue';

// posicion inicial de los dos jugadores 
const positionPlayerOne=5;
const positionPlayerTwo=77;

// lo que voy a hacer es traerme a i para poder cambiar el valor de esos cuadrados con un if 

const props = defineProps({
    // aqui estaran las id que necesito para modificar el color 
    id: {
        type: Number,
        // lo que required no entiendo pa que xd 
        required: true
    }
});

</script>

<template>
    <!-- aplica el estilo solo si  -->
    <section class="cuadrado" 
    :class="{ 'cuadrado': true, 'cuadrado-one': id === positionPlayerOne , 'cuadrado-two': id === positionPlayerTwo}">
    <!-- tener en cuenta que para traer valores de otro componente estos tienen que llamarse igual al que puse en el v-bind :playerId por ejemplo debe coincidir con el prop  -->

        <!-- solo se renderiza si  -->
        <Player :playerId=1 v-if="id === positionPlayerOne"/>
        <!-- id que identifica cada una para luego estilizarlo  -->
        <Player :playerId=2 v-if="id === positionPlayerTwo"/>
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
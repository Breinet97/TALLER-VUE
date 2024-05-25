<script setup>
    import { ref, onMounted } from 'vue';

    import Player from './player.vue';

    // arreglo para el tablero 
    const cuadrados = ref([]);

    // posicion inicial de los jugadores en los cuadrados 
    const playerOnePosition = 5;
    const playerTwoPosition = 77;

    // for para crear el componente del cuadrado 9*9
    onMounted(() => {
        for (let i = 0; i < 81; i++) {
            // mientras esta creando los cuadrados debe verificar si es la posicion incial de cada jugador, si llega hacerlo agrega al jugador a esa posicion PERO SI NO 
            // sigue creando los cuadrados 

            if(i === playerOnePosition || i === playerTwoPosition){
                cuadrados.value.push(
                    {
                        player: i === playerOnePosition? 1:2
                    }
                )
            }else{
                cuadrados.value.push({player:null});
            }
        }
    });
</script>

<template>
    <section class="cuadrado" 
            v-for="(cuadrado, index) in cuadrados" 
            :key="index"
            >
            <Player/>
    </section>
</template>

<style scoped>
.cuadrado {
    /* 
    para reconocer el turno dle jugador lo que haremos es un truco:
    sabremos que pulsan teniendo simbolos y encima la imagen, asi sabre el turno y ganador  */

    position: relative;

    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 5px solid black;
    background-color: rgba(0, 0, 0, 0.699);
    font-size: 18px;
}
</style>
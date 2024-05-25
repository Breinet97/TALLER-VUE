<script setup>
import { ref, onMounted } from 'vue';

// arreglo para el tablero 
const cuadrados = ref([]);


onMounted(() => {
    for (let i = 0; i < 81; i++) {
        cuadrados.value.push({});
    }
});

</script>

<template>
    <h1>Videogame</h1>

    <main class="main-tablero">
        <section class="tablero" id="tablero">
            <section
            class="cuadrado" 
            v-for="(cuadrado, index) in cuadrados" 
            id="cuadrado"
            :key="index"
            >
            </section>
        </section>
    </main>
</template>

<style scoped>
.tablero {
    display: grid;
    gap: 2px;
    grid-template-columns: repeat(9, 1fr);

}

.cuadrado {
    /* width: 50px; */
    height: 50px;
    /* padding: 2rem; */
    display: flex;
    justify-content: center;
    align-items: center;
    border: 5px solid black;
    background-color: black;
    font-size: 18px;
}
</style>
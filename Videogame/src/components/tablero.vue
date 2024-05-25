<script setup>
// import { ref, onMounted } from 'vue';
import Cuadrado from './cuadrado.vue';

</script>

<template>
    <main class="main-tablero">
        <section class="tablero" id="tablero">
            <cuadrado/>
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
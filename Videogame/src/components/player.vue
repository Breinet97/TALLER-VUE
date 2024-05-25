<script setup>

import { ref, computed } from 'vue';

const props = defineProps({
    player:{
        type: Number,
        default: null
    }
})

// Clase CSS para el color del jugador
const playerClass = computed(() => {
  return props.player === 1 ? 'playerOne' : (props.player === 2 ? 'playerTwo' : '');
});



</script>
<template>
    <section class="field" :class="playerClass">
        
    </section>

</template>
<style scoped>
.field {
    position: absolute;
    background-color: red;
    width: 75px;
    height: 75px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.playerOne {
  background-color: blue;
}

.playerTwo {
  background-color: orange;

}

</style>

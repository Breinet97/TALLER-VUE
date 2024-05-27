<script setup>

const props = defineProps({
    // aqui estaran las id que necesito para modificar el color 
    playerId: {
        type: Number,
        // lo que required no entiendo pa que xd 
        required: true
    }
});
</script>
<template>
  <!-- cada jugador tiene un id independiente asi logro ponerle estilos diferentes a cada uno -->
  <section 
  :class="{ 'player': true, 'player-one': playerId === 1 , 'player-two': playerId === 2}">
  </section>

</template>
<style scoped>
.player {
  width: 90%;
  height: 100%;
  /* position: absolute; */
}
.player-one {
  background: url(../assets/images/Kirby-Player.png);
  background-position: center;
  background-size: cover;
}

.player-two {
 
  background: url(../assets/images/Toad-Player.png);
  background-position: center;
  background-size: cover;

}
</style>

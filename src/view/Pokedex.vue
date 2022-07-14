<template>
  <v-container class="container">
    <v-img
      class="pokedex-image"
      width="800" 
      :src="require('@/assets/pokedex.png')"
    >
    </v-img>
    <v-card class="pokemon-card"></v-card>
  </v-container>
</template>

<script>
export default {

}
</script>

<style scoped>
  .pokedex-image{
    margin: 0 auto !important;
    z-index: 2;
  }
  .pokemon-card{
    background-color: #fff;
    width: 255px;
    height: 170px;
    position: absolute;
    top: 365px;
    left: 635px;
  }
</style>
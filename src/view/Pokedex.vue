<template>
  <v-container class="container">
    <v-img
      class="pokedex-image"
      width="800" 
      :src="require('@/assets/pokedex.png')"
    >
    </v-img>
    <v-card class="pokemon-card">
      <v-container class="pokemon-container">
        <img 
          :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-v/black-white/animated/${idPokemon}.gif`"
          :alt="1"
          width="50%"
        />
        <!-- <h2 class="text-center">1</h2> -->
      </v-container>
    </v-card>
    <v-btn 
      depressed 
      class="btn-navigation-previous" 
      color="error" 
      @click="previousPokemon()"
    >
      previous
    </v-btn>
    <v-btn 
      depressed 
      class="btn-navigation-next" 
      color="success" 
      @click="nextPokemon()"
    >
      Next
    </v-btn>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    idPokemon: 1
  }),

  methods:{
    nextPokemon(){
      this.idPokemon++
    },
    previousPokemon(){
      this.idPokemon--
    }
  }
}
</script>

<style scoped>
  .pokedex-image{
    margin: 0 auto !important;
    z-index: 2;
  }
  .pokemon-container{
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .pokemon-card{
    display: flex;
    align-items: center;
    background-color: #fff;
    width: 255px;
    height: 170px;
    position: absolute;
    top: 365px;
    left: 635px;
  }
  .btn-navigation-previous{
    position: absolute;
    bottom: 244px;
    right: 748px;
    height: 45px !important;
    min-width: 120px !important;
    z-index: 3;
  }
  .btn-navigation-next{
    position: absolute;
    bottom: 244px;
    right: 610px;
    height: 45px !important;
    min-width: 120px !important;
    z-index: 3;
  }
</style>
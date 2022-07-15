<template>
  <v-container class="container">
    <v-img
      class="pokedex-image"
      width="800" 
      :src="require('@/assets/pokedex.png')"
    >
    </v-img>
    <ScreenPokemon 
      :idPokemon="idPokemon"
    />
    <ScreenNamePokemon 
      :namePokemon="pokemons.name"
    />
    <v-btn
      class="btn-navigation-previous" 
      @click="previousPokemon()"
    >
      previous
    </v-btn>
    <v-btn 
      class="btn-navigation-next" 
      @click="nextPokemon()"
    >
      Next
    </v-btn>
  </v-container>
</template>

<script>
import axios from 'axios'
import ScreenPokemon from "@/components/ScreenPokemon"
import ScreenNamePokemon from "@/components/ScreenNamePokemon"
export default {
  components:{
    ScreenPokemon,
    ScreenNamePokemon,
  },

  data: () => ({
    idPokemon: 1,
    pokemons: []
  }),

  mounted(){
    this.fetchPokemon(this.idPokemon)
  },

  methods:{
    async fetchPokemon(id){
      await axios.get(`https://pokeapi.co/api/v2/pokemon/${id}`).then((response) => {
        this.pokemons = response.data;
      })
    },

    nextPokemon(){
      this.idPokemon++
      this.fetchPokemon(this.idPokemon)
    },

    previousPokemon(){
      if(this.idPokemon != 1) return this.idPokemon--
      this.fetchPokemon(this.idPokemon)
    }
  },

  
}
</script>

<style scoped>
  .pokedex-image{
    margin: 0 auto !important;
    z-index: 2;
  }

  .btn-navigation-previous{
    position: absolute;
    bottom: 244px;
    right: 748px;
    height: 43px !important;
    min-width: 120px !important;
    color: #fff !important;
    background: #ce0321 !important;
    border: 2px solid #000606 !important;
    border-radius: 9px !important;
    box-shadow: none !important;
    z-index: 3;
  }

  .btn-navigation-next{
    position: absolute;
    bottom: 244px;
    right: 610px;
    height: 43px !important;
    min-width: 120px !important;
    color: #fff !important;
    background: #0b7082 !important;
    border: 2px solid #000606 !important;
    border-radius: 9px !important;
    box-shadow: none !important;
    z-index: 3;
  }
</style>
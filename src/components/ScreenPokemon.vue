<template>
  <v-card class="pokemon-card">
      <v-container class="pokemon-container">
        <img 
          :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-v/black-white/animated/${idPokemon}.gif`"
          :alt="1"
          width="43%"
        />
      </v-container>
    </v-card>
</template>

<script>
// import axios from 'axios'
export default {
  props:{
    idPokemon:{
      type: [Number, String]
    }
  },
  
  data: () => ({

  }),

  methods:{

  }
}
</script>

<style scoped>
  .pokemon-container{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .pokemon-card{
    display: flex;
    align-items: center;
    background-color: #a0fdff !important;
    width: 255px;
    height: 170px;
    position: absolute;
    top: 365px;
    left: 635px;
  }
</style>
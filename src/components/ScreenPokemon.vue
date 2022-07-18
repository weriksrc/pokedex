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
    width: 17.5%;
    height: 25%;
    position: absolute;
    top: 33.5%;
    left: 29.5%;
  }
</style>
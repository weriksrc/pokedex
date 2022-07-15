<template>
  <v-card class="pa-1 card-name">
    <v-card-title class="pa-1 name-pokemon">
      {{ getName(namePokemon) }}
    </v-card-title>
  </v-card>
</template>

<script>

export default {

  props:{
    namePokemon: {
      type: String
    }
  },

  data: () => ({

  }),

  methods:{
    getName(name){
      console.log(name);
      return name.charAt(0).toUpperCase() + name.substring(1)
    },
  },

}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

  .card-name{
    position: absolute;
    bottom: 235px;
    left: 658px;
    width: 133px !important;
    height: 63px;
    z-index: 3;
    display: flex;
    background-color: #084035 !important;
    color: #53ac57 !important;
    font-family: 'Press Start 2P', cursive;
    justify-content: center;
    border: 2px solid #000606 !important;
    border-radius: 9px !important;
    box-shadow: none !important;
  }

  .name-pokemon{
    font-size: 0.65rem;
  }

</style>
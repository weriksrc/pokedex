<template>
  <v-app>
    <Pokedex />
  </v-app>
</template>

<script>
import Pokedex from '@/view/Pokedex.vue';
export default {
  components: { Pokedex },
  name: 'App',
};
</script>

<style>
#app {
  background: linear-gradient(
      to bottom right,
      rgba(10, 10, 10, 1),
      rgba(12, 39, 63, 1)
    )
    no-repeat center center fixed !important;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover !important;
  background-position: center;
  min-height: 100vh;
  justify-content: space-evenly;
}
.v-application--wrap{
  justify-content: space-evenly ;
}
</style>

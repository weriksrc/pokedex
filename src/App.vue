<template>
  <v-app>
      <v-container>
        <v-text-field
          v-model="search"
          label="Pesquisar"
          solo
        >
        </v-text-field>
        <v-row>
          <v-col 
            cols="2" 
            v-for="pokemon in filteredPokemons" 
            :key="pokemon.name"
          >
          <v-card @click="showPokemonInfo(pokemon)">
            <v-container>
              <v-row class="mx-0 d-flex justify-center">
              <img 
                :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${getId(pokemon)}.png`"
                :alt="pokemon.name"
                width="80%"
              />
              </v-row>
              <h2 class="text-center">{{ getName(pokemon) }}</h2>
            </v-container>
          </v-card>
          </v-col>
        </v-row>
      </v-container>
      <v-dialog
      v-model="showDialog"
      width="800"
    >
      <v-card v-if="selectedPokemon" class="px-4">
        <v-container>
          <v-row class="d-flex align-center">
            <v-col cols="4">
              <img 
                :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${selectedPokemon.id}.png`"
                :alt="selectedPokemon.name"
                width="80%"
              />
            </v-col>
            <v-col cols="8">
              <h1>{{ getName(selectedPokemon) }}</h1>
              <v-chip label class="mr-2" v-for="type in selectedPokemon.types" :key="type.slot">{{ type.type.name }}</v-chip>
              <v-divider class="my-4"></v-divider>
              <v-chip label>Altura {{ selectedPokemon.height * 2.54}} cm</v-chip>
              <v-chip label class="ml-2">Peso {{ (selectedPokemon.weight * 0.45359237).toFixed(0) }} kg</v-chip>
            </v-col>
          </v-row>

          <h2>Moves</h2>
          <v-simple-table>
            <template>
              <thead>
                <tr>
                  <th class="text-left">
                    Level
                  </th>
                  <th class="text-left">
                    Name
                  </th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="item in filterMoves(selectedPokemon)"
                  :key="item.move.name"
                >
                  <td>{{ getMoveLevel(item) }}</td>
                  <td>{{ item.move.name }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </v-container>
      </v-card>
    </v-dialog>
  </v-app>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',

  data: () => ({
    pokemons: [],
    search: "",
    showDialog: false,
    selectedPokemon: null
  }),

  mounted(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151").then((response) => {
      this.pokemons = response.data.results;
    })
  },

  methods:{
    getId(pokemon){
      return Number(pokemon.url.split("/")[6])
    },

    getName(pokemon){
      return pokemon.name.charAt(0).toUpperCase() + pokemon.name.substring(1)
    },

    showPokemonInfo(pokemon){
      let idPokemon = this.getId(pokemon);

      axios.get(`https://pokeapi.co/api/v2/pokemon/${idPokemon}`).then((response) => {
        this.showDialog = !this.showDialog;
        this.selectedPokemon = response.data;
    })
    },

    getMoveLevel(move){
      for(let version of move.version_group_details){
        if(version.version_group.name == "sword-shield" && version.move_learn_method.name == "level-up"){
            return version.level_learned_at;
          }
      }
      return 0
    },

    filterMoves(pokemon){
      return pokemon.moves.filter((item) =>{
        let include = false;
        for (let version of item.version_group_details){
          if(version.version_group.name == "sword-shield" && version.move_learn_method.name == "level-up"){
            include = true;
          }
        }
        return include
      })
    }
  },

  computed:{
    filteredPokemons(){
      return this.pokemons.filter((item) => {
        return item.name.includes(this.search)
      })
    }
  }
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
}
</style>

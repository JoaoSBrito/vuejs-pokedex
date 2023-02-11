<script setup>
import { computed, onMounted, ref, watch } from "vue"

// import PokemonStats from './PokemonStats.vue';
const pokemon = defineProps(["name", "img", "height", "weight", "types", "stats", "species"])

  const capitalizedName = computed(() => {
    return pokemon.name && pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1)
  })

    const capitalizedStat = (stat) => {
      return stat.stat.name.charAt(0).toUpperCase() + stat.stat.name.slice(1) + ":"
    }

    const statsColors = {
      hp: "#f44336",
      attack: "#ff9800",
      defense: "#ffeb1b",
      "special-attack": "#2196f3",
      "special-defense": "#4caf50",
      speed: "#e91e63",
    }

    const statColor = (stat) => {
      return statsColors[stat.stat.name]
    }

    const capitalizedType = (type) => {
      return type.type.name.charAt(0).toUpperCase() + type.type.name.slice(1)
    }

    const typeColor = (type) => {
      return typeColors[type.type.name]
    }

    const typeColors = {
      normal: '#A8A77A',
      fire: '#EE8130',
      water: '#6390F0',
      electric: '#F7D02C',
      grass: '#7AC74C',
      ice: '#96D9D6',
      fighting: '#C22E28',
      poison: '#A33EA1',
      ground: '#E2BF65',
      flying: '#A98FF3',
      psychic: '#F95587',
      bug: '#A6B91A',
      rock: '#B6A136',
      ghost: '#735797',
      dragon: '#6F35FC',
      dark: '#705746',
      steel: '#B7B7CE',
      fairy: '#D685AD',
    }


</script>



<template>
  

  <!-- <div class="pokemon-infos"> -->
    
    <!-- Modal -->
    <div class="modal fade" id="pokeModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content d-flex justify-content-center">
          <div class="modal-header">
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <div class="">
              <div class="head text-center">
              <img :src="img" alt="" height="140">
              <h1 class="mt-4 fw-bold">
                {{ capitalizedName }}
              </h1>
              <ul class="px-4 mt-4 text-center d-flex align-items-center justify-content-center gap-5 ">
                <li class="text-white text-center list-unstyled" v-for="type in pokemon.types" :key="type.type.name">
                  <span class="p-2 fw-bold rounded" :style="{ backgroundColor: typeColor(type), fontFamily: 'Roboto Serif' }" v-text="capitalizedType(type)"> </span>
                </li>
              </ul>
              </div>

              <hr>

              <div class="infos">
                <div class="personal d-flex align-items-center justify-content-center gap-5">
                <p>{{pokemon.height * 2.54}}cm</p>
                <p>{{pokemon.weight * 0.45359237.toFixed(1)}}kg</p>
                
                </div>

                
                <!-- <p>{{pokemon.stats}}</p> -->
              </div>

              <div class="stats">
                <h1 class="">Stats</h1>
                <div class="list d-flex align-items-center justify-content-center" style="width: 100%">
                  <ul class="text-center d-flex-colum align-items-center justify-content-center gap-5" style="max-width: 80vw">
                    <li class="text-white d-flex justify-content-center align-items-center gap-2 px-4 py-2 rounded mb-3" v-for="(stat) in pokemon.stats" :key="stat.stat.name" :style="{ backgroundColor: statColor(stat)}">
                      <span class="" label v-text="capitalizedStat(stat)" /> 
                      <span class="">{{ stat.base_stat}}</span>
                    
                  </li>
                </ul>
              </div>
              </div>

              <hr>

              <div class="evolutions">
                <h1 class="">Evolutions</h1>
                <div class="evolution-content p-2">
                  {{ pokemon.species }}
                </div>
              </div>


            </div>
          </div>
        </div>
      </div>
    </div>
  
</template>

<style scoped>
h1 {
  font-family: 'Roboto Serif';
  font-weight: bold;
}

</style>
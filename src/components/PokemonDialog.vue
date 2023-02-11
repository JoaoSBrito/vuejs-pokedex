<script setup>
import { computed, onMounted, ref, watch } from "vue"

// import PokemonStats from './PokemonStats.vue';
const pokemon = defineProps(["name", "img", "height", "weight", "types", "stats", "species"])


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
              <h1 class="mt-4">
                {{ pokemon.name }}
              </h1>
              <ul class="px-4 mt-4 text-center d-flex align-items-center justify-content-center gap-5 ">
                <li class=" text-center list-unstyled" v-for="type in pokemon.types" :key="type.type.name">
                  <span>{{  type.type.name }} </span>
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

              <div class="stats mt-2">
                <h1 class="">Stats</h1>
                <ul class="d-flex-colum align-items-center">
                  <li class="list-unstyled my-2" v-for="(stat) in pokemon.stats" :key="stat.stat.name">
                    <span class="" label>{{stat.stat.name}}: {{ stat.base_stat}}</span> 
                  </li>
                </ul>
              </div>

              <hr>

              <div class="evolutions">
                <h1>Evolutions</h1>
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

</style>
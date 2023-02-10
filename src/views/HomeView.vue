<script setup>
  import { onMounted, reactive, ref } from 'vue'
  import PokemonList from '../components/PokemonList.vue';

  let pokemons = reactive(ref())

  onMounted(() => {
      fetch("https://pokeapi.co/api/v2/pokemon?limit=100000&offset=0")
      .then(res => res.json())
      .then(res => pokemons.value = res.results)
  })
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12 col-md-6">
        <div class="card">
          <PokemonList
            v-for="pokemon in pokemons"
            :key="pokemon.name"
            :name="pokemon.name"
          />
          <!-- <ul>
            <li 
              v-for="pokemon in pokemons"
              :key="pokemon.name"
            >{{pokemon.name}}</li>
          </ul> -->
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
  import { onMounted, reactive, ref, computed } from 'vue'
  import PokemonList from '../components/PokemonList.vue';
  import PokemonDialog from '../components/PokemonDialog.vue';

  let pokemons = reactive(ref())
  let urlBaseSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/")
  let searchForPokemon = ref("")
  let selectedPokemon = reactive(ref())

  onMounted(() => {
      fetch("https://pokeapi.co/api/v2/pokemon?limit=400&offset=0")
      .then(res => res.json())
      .then(res => pokemons.value = res.results)
  })

  const filteredPokemons = computed(() => {
    if(pokemons.value && searchForPokemon.value) {
      return pokemons.value.filter(pokemon => pokemon.name.toLowerCase().includes(searchForPokemon.value.toLowerCase()))
    }
    return pokemons.value
  })

  const selectPokemon = async (pokemon) => {
    await fetch(pokemon.url)
      .then(res => res.json())
      .then(res => selectedPokemon.value = res)

      console.log(selectedPokemon.value)
  }

</script>

<template>
  <div class="container">

    <PokemonDialog 
      :name="selectedPokemon?.name"
    />


    <div class="mb-3">
      <label 
        hidden 
        for="searchPokemon" 
        class="form-label">
        Digite o nome do Pokemon...
      </label>

      <input 
        v-model="searchForPokemon"
        type="text" 
        class="form-control" 
        id="searchPokemon" 
        placeholder="Digite o nome do Pokemon..."
        />
    </div>
    <div class="row">
      <div class="col-sm-12 col-md-6">
        <div class="card card-list">
          <div class="card-body row">

          <PokemonList
            v-for="pokemon in filteredPokemons"
            :key="pokemon.name"
            :name="pokemon.name"
            :alt="pokemon.name"
            :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
            @click="selectPokemon(pokemon)"
          />
        </div>
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

<style scoped>
  .card-list {
    overflow-x: hidden;
    overflow-y: scroll;
    max-height: 350px;
  }
</style>
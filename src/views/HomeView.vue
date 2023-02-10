<script setup>
  import { onMounted, reactive, ref } from 'vue'
  import PokemonList from '../components/PokemonList.vue';

  let pokemons = reactive(ref())
  let urlBaseSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/")

  onMounted(() => {
      fetch("https://pokeapi.co/api/v2/pokemon?limit=400&offset=0")
      .then(res => res.json())
      .then(res => pokemons.value = res.results)
  })
</script>

<template>
  <div class="container">
    <div class="logo">
      <img src="@/assets/logo.png" alt="">
    </div>
    <div class="row">
      <div class="col-sm-12 col-md-6">
        <div class="card">
          <div class="card-body row">

            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Email address</label>
              <input type="email" class="form-control" id="exampleFormControlInput1" placeholder="name@example.com">
            </div>
          <PokemonList
            v-for="pokemon in pokemons"
            :key="pokemon.name"
            :name="pokemon.name"
            :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
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
<script setup>
  const pokemon = defineProps(["name", "urlBaseSvg"])
  
  const getName= (pokemon) => {
    return pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1)
  }
</script>

<template>
  <div class="col-6">
    <div class="card mb-3 p-2 w">
      <img 
        class="card-img"
        :src="urlBaseSvg" alt=""
        height="80"
        />
      <p class="text-center mt-2 mb-0 fw-bold">{{ getName(pokemon) }}</p>
    </div>
  </div>
</template>

<style>
  .card {
    font-family: 'Roboto Serif';
    width: 100%;
    cursor: pointer;
  }

  .card img:hover {
    transform: scale(1.1);
  }
</style>
<script></script>

<template>
  <nav class="navbar navbar-expand-lg ">
    <div class="container-fluid d-flex align-items-center">
      <router-link class="navbar-brand text-white d-flex align-items-center gap-2" to="/">
        <img src="@/assets/pokeball.svg" alt="" class="img-fluid">
        Pokedex
      </router-link>
      <button class="navbar-toggler border-white" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon" style="color:white"></span>
      </button>
      <div class="collapse navbar-collapse text-center " id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link text-white" aria-current="page" to="/">Ínicio</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link text-white" to="/about">Sobre</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <div class="main">
    <router-view></router-view>
  </div>

</template>

<style>
  body {
    background-color: #C23D3D;
    font-family: 'Inter';
  }
</style>
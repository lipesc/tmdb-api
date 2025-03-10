<script setup>
import { ref, watchEffect } from 'vue';
import MovieList from './components/MovieList.vue'

const movies = ref([]);
const currentPage = ref(1);
const searchResults = ref([]);
const searchQuery = ref("");


// top 10 movies buscar
const topMovies = async (page) => {
  try {
    const response = await fetch(`http://localhost:8080/movies/top/${page}`);
    const data = await response.json();
    movies.value = data.results;
  } catch (error) {
    console.error("erro ao buscar filmes: ", error);
  }
}

// pesquisar filme por titulo

const searchMoviesTitle = async (query) => {
  if (!query) return;
  try {
    
    const response = await fetch(`http://localhost:8080/movies/search/${query}`);
    const data = await response.json();
    searchResults.value = data.results;

  } catch (error) {
    console.log("erro ao buscas o filmes: ", error);
    
  }
};

// montagem para carregar filmes
watchEffect(() => {
  topMovies(currentPage.value);
});

// monitorar input de buscar

watchEffect(() => {
  if (searchQuery.value.trim()) {
    searchMoviesTitle(searchQuery.value);
  }
});

</script>

<template>
  
<div class="header">
  <div class="logo">
    <img alt="logo" height="30" src="./assets/icons8-github-64.png" width="30"/>
    <span>
      <a href="https://github.com/lipesc" target="_blank">lipesc</a>
    </span>
  </div>

  <div class="search-container">
    <input type="text" v-model="searchQuery" placeholder="Pesquisar filme" />
  </div>
</div>

  <h1>Filmes tmdb</h1>

  <div id="search-movies-container">
    <div v-if="searchResults.length">
      <h3>filmes encontrados</h3>
      <MovieList :movies="searchResults"/>
    </div>
  </div>


  <h3>Top filmes de hoje</h3>
  <MovieList :movies="movies"/>

  <button @click="currentPage++">Proxima pagina</button>


</template>

<style>


</style>

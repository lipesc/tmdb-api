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
    const response = await fetch(`/movies/top/${page}`);
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
    
    const response = await fetch(`/movies/search/${query}`);
    const data = await response.json();
    searchResults.value = data.results;

  } catch (error) {
    console.log("erro ao buscas o filmes: ", error);
    
  }
};


</script>

<template>
  

</template>

<style scoped>

</style>

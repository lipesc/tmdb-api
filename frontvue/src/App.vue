<script setup>
import { ref, watchEffect } from 'vue';
import MovieList from './components/MovieList.vue'

const movies = ref([]);
const currentPage = ref(1);
const searchResults = ref([]);
const searchQuery = ref("");

const topMovies = async (page) => {
  try {
    const response = await fetch(`/movies/top/${page}`);
    const data = await response.json();
    movies.value = data.results;
  } catch (error) {
    console.error("erro ao buscar filmes: ", error);
  }
}

</script>

<template>
  

</template>

<style scoped>

</style>

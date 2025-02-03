<script setup>


defineProps({
  movies: Array,
})


</script>

<template>
  <div v-for="movie in movies" :key="movie.id" class="movie">
    <img :src="'https://image.tmdb.org/t/p/original' + movie.poster_path" alt="poster movie" />
    <h3>Filme: {{ movie.title }}</h3>
    <p>Titulo original: {{ movie.original_title }}</p>
    <p>Resumo: {{ movie.overview }}</p>
    <p>Lançamento: {{ movie.release_date }}</p>
    <p>Nota: {{ movie.vote_average }}</p>
  </div>
</template>

<style scoped>
.movie {
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 10px;
  background: white;
}
</style>

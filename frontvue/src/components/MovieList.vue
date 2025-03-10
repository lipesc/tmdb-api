<script setup>


defineProps({
  movies: Array,
})


</script>

<template>

  <div class="movie-list">

    <div v-for="movie in movies" :key="movie.id" class="movies-container">
      <img :src="'https://image.tmdb.org/t/p/original' + movie.poster_path" alt="poster movie" width="250" height="350" />
      

    <div class="movie-info">

      <h3>{{ movie.title }}</h3>
      <p><i>Titulo original:</i> {{ movie.original_title }}</p>
      <p><i>Resumo:</i> {{ movie.overview }}</p>
      <p><i>Lançamento:</i> {{ movie.release_date }}</p>
      <p><i>Nota:</i> {{ movie.vote_average }}</p>
    
    </div>
  </div>
</div>
</template>

<style scoped>
.movie-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Ensures proper wrapping */
  gap: 15px;
  padding: 20px;
  justify-content: center;
}

.movie {
  background: #141414;
  color: white;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
  text-align: center;
  width: 100%;
}

.movie:hover {
  transform: scale(1.05);
}

.movie img {
  width: 100%;
  height: 225px; /* Maintain proportion */
  object-fit: cover;
  border-bottom: 3px solid #e50914; /* Netflix-style red */
}

.movie-info {
  padding: 10px;
  font-size: 0.85rem;
}
.movie-info h3 {
  color: #e50914;
}


@media (min-width: 768px) {
  .movie-list {
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); /* Slightly larger on bigger screens */
  }
}

@media (min-width: 1024px) {
  .movie-list {
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); /* More space on desktops */
  }
}
</style>
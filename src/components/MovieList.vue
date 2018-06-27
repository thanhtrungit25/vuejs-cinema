<template>
  <div id="movie-list">
    <movie-item v-for="(movie, index) in filteredMovies" :key="index" v-bind:movie="movie" class="movie"></movie-item>
  </div>
</template>
<script>
import genres from '../util/genres';
import MovieItem from './MovieItem.vue';

export default {
  props: ['genre', 'time', 'movies'],
  methods: {
    moviePassesGenderFilter(movie) {
      if (!this.genre.length) {
        return true;
      } else {
        return this.genre.find(genre => movie.genre === genre);
      }
    },
  },
  computed: {
    filteredMovies() {
      return this.movies.filter(this.moviePassesGenderFilter);
    },
  },
  components: {
    MovieItem,
  },
};
</script>

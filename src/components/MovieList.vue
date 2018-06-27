<template>
  <div id="movie-list">
    <div v-for="(movie, index) in filteredMovies" :key="index" class="movie">{{ movie.title }}</div>
  </div>
</template>
<script>
import genres from '../util/genres';

export default {
  props: ['genre', 'time'],
  data: function() {
    return {
      movies: [
        { title: 'Kill Bill', genre: genres.CRIME },
        { title: 'Home Alone', genre: genres.COMEDY },
        { title: 'Austin Powers', genre: genres.COMEDY },
      ],
    };
  },
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
};
</script>

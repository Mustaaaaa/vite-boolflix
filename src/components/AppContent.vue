<template>
  <div>
    <AppHeader @search="searchMovies" />
    <AppMovieList :movies="movies" />
  </div>
</template>

<script>
import axios from 'axios';
import AppHeader from './AppHeader.vue';
import AppMovieList from './AppMovieList.vue';

export default {
  data() {
    return {
      movies: []
    };
  },
  methods: {
    searchMovies(searchQuery) {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'd395d14d3880da643f4fd372aabbbd48',
          query: searchQuery
        }
      })
        .then(res => {
          this.movies = res.data.results.map(movie => ({
            id: movie.id,
            title: movie.title,
            original_title: movie.original_title,
            original_language: movie.original_language,
            vote_average: movie.vote_average,
            image_url: movie.poster_path ? `https://image.tmdb.org/t/p/w200${movie.poster_path}` : 'placeholder_image_url.jpg'
          }));
        })
    }
  },
  components: {
    AppHeader,
    AppMovieList
  }
};
</script>

<style lang="scss"></style>

<template>
  <div>
    <AppHeader @search="searchMovies" />
    <AppMovieList :movies="movies" />
    <AppMovieList :series="series" />
  </div>
</template>

<script>
import axios from 'axios';
import AppHeader from './AppHeader.vue';
import AppMovieList from './AppMovieList.vue';

export default {
  data() {
    return {
      movies: [],
      series: []
    };
  },
  methods: {
    searchMovies(searchQuery) {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'd395d14d3880da643f4fd372aabbbd48',
          query: searchQuery
        },
      })
        .then(res => {
          this.movies = res.data.results.map(movie => ({
            title: movie.title,
            original_title: movie.original_title,
            original_language: movie.original_language,
            vote_average: movie.vote_average,
            overview: movie.overview,
            image_url: movie.poster_path ? `https://image.tmdb.org/t/p/w200${movie.poster_path}` : '',
            type: 'movie'
          }));
        })

      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: 'd395d14d3880da643f4fd372aabbbd48',
          query: searchQuery
        },
      })
        .then(res => {
          this.series = res.data.results.map(serie => ({
            title: serie.name,
            original_title: serie.original_name,
            original_language: serie.original_language,
            vote_average: serie.vote_average,
            overview: serie.overview,
            image_url: serie.poster_path ? `https://image.tmdb.org/t/p/w200${serie.poster_path}` : '',
            type: 'tv'
          }));
        })
    },
  },
  components: {
    AppHeader,
    AppMovieList
  }
};
</script>

<style lang="scss"></style>

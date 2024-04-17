<template>
    <ul class="movie-list">
        <li v-for="movie in movies" class="movie-item">
            <h2>{{ movie.title }}</h2>
            <img :src="movie.image_url" alt="">
            <p><strong>Titolo:</strong> {{ movie.title }}</p>
            <p><strong>Titolo Originale:</strong> {{ movie.original_title }}</p>
            <p><strong>Lingua:</strong> {{ movie.original_language }}</p>
            <p><strong>Voto:</strong> {{ movie.vote_average }}</p>
        </li>
    </ul>
</template>

<script>
export default {
    props: ['movies']
};
</script>

<style lang="scss">

</style>
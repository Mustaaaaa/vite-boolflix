<template>
    <div class="main-content">
        <div class="container">
            <div class="row">
                <div class="col-4" v-for="movie in movies">
                    <div class="movie-item">
                        <h2>{{ movie.title }}</h2>
                        <img :src="movie.image_url" alt="" class="movie-image">
                        <p><strong>Titolo:</strong> {{ movie.title }}</p>
                        <p><strong>Titolo Originale:</strong> {{ movie.original_title }}</p>
                        <p><strong>Lingua:</strong> <img :src="getFlagImage(movie.original_language)" alt=""> {{ getLanguageName(movie.original_language) }}</p>
                        <p><strong>Voto:</strong> {{ movie.vote_average }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    props: ['movies'],
    data() {
        return {
            flagImages: {
                'en': '../../public/en.png',
                'it': '../../public/it.png',
                'br': '../../public/br.png',
                'ja': '../../public/jp.png',
                'ch': '../../public/ch.png',
                'es': '../../public/es.png',
            }
        };
    },
    methods: {
        getFlagImage(language) {
            return this.flagImages[language] || language;
        },
        getLanguageName(language) {
            return this.flagImages[language] ? '' : language;
        },
    }
};
</script>

<style lang="scss">
.movie-item {
    color: white;
    .movie-image {
        display: block;
        margin-left: auto;
        margin-right: auto;
    };

    h2 {
        text-align: center;
    };

    p {
        img {
            width: 30px;
        };
    };
};
</style>
<!-- :src="movie.image_url" -->
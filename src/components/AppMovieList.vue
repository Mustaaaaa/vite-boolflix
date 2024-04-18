<template>
    <div class="main-content">
        <div class="container">
            <div class="row">
                <div class="col-4" v-for="movie in movies">
                    <div class="movie-item">
                        <div class="image-container">
                            <img :src="movie.image_url" alt="" class="movie-image">
                            <div class="overlay">
                                <p><strong>Titolo:</strong> {{ movie.title }}</p>
                                <p><strong>Titolo Originale:</strong> {{ movie.original_title }}</p>
                                <p><strong>Lingua:</strong> <img :src="getFlagImage(movie.original_language)" alt=""> {{
                                    getLanguageName(movie.original_language) }}</p>
                                <p><strong>Voto:</strong> {{ movie.vote_average }}</p>
                                <p><strong>Overview:</strong> {{ movie.overview }}</p>
                                <p><strong>Type:</strong> {{ movie.type }}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-4" v-for="serie in series">
                    <div class="movie-item">
                        <div class="image-container">
                            <img :src="serie.image_url" alt="" class="movie-image">
                            <div class="overlay">
                                <p><strong>Titolo:</strong> {{ serie.title }}</p>
                                <p><strong>Titolo Originale:</strong> {{ serie.original_title }}</p>
                                <p><strong>Lingua:</strong> <img :src="getFlagImage(serie.original_language)" alt=""> {{
                                    getLanguageName(serie.original_language) }}</p>
                                <p><strong>Voto:</strong> {{ serie.vote_average }}</p>
                                <p><strong>Overview:</strong> {{ serie.overview }}</p>
                                <p><strong>Type:</strong> {{ serie.type }}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    props: ['movies', 'series'],
    data() {
        return {
            flagImages: {
                'en': '../../public/en.png',
                'it': '../../public/it.png',
                'br': '../../public/br.png',
                'ja': '../../public/jp.png',
                'cn': '../../public/ch.png',
                'es': '../../public/es.png',
            }
        };
    },
    methods: {
        getFlagImage(language) {
            return this.flagImages[language] || '';
        },
        getLanguageName(language) {
            return this.flagImages[language] ? '' : language.toUpperCase();
        },
    }
};
</script>

<style lang="scss">
.main-content {
    background-color: rgb(26, 25, 25);
}

.movie-item {
    color: white;

    .image-container {
        position: relative;
        overflow: hidden;
        margin: 10px;

        .movie-image {
            display: block;
            width: 345px;
            height: 500px;
            transition: transform 0.5s;
        }

        .overlay {
            position: absolute;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.589);
            display: flex;
            flex-direction: column;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.5s;

            p {
                padding: 10px 15px;
            }
        }

        &:hover {
            .movie-image {
                transform: scale(1.1);
            }

            .overlay {
                opacity: 1;
            }
        }
    }

    h2 {
        text-align: center;
    }

    p {
        img {
            width: 30px;
        }
    }
}

;
</style>
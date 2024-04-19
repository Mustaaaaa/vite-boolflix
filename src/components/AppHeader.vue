<template>
    <div class="header-bar">
        <div class="row">
            <div class="logo">
                <h1>BOOLFLIX</h1>
            </div>
            <div class="vision-option display-none">
                <ul class="row gap-15">
                    <li class="display-none-md"><a href="#">Home</a></li>
                    <li class="display-none-md"><a href="#">Serie TV</a></li>
                    <li class="display-none-md"><a href="#">Film</a></li>
                    <li class="display-none-md"><a href="#">Originali</a></li>
                    <li class="display-none-md"><a href="#">Aggiunti di recente</a></li>
                    <li class="display-none-md"><a href="#">La mia lista</a></li>
                </ul>
            </div>
        </div>
        <div class="search-bar">
            <input type="text" v-model="searchQuery" placeholder="Cerca un film o una Serie...">
            <button @click="search">Cerca</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            searchQuery: ''
        };
    },
    methods: {
        search() {
            this.$emit('search', this.searchQuery);
        }
    }
};
</script>

<style lang="scss">
.header-bar {
    padding: 20px 20px 40px 20px;
    align-items: center;
    background-color: rgb(26, 25, 25);

    .logo {
        margin-right: 40px;
        color: red
    }

    .vision-option {
        display: flex;
        align-items: center;

        a {
            text-decoration: none;
            color: white;
            padding: 10px;
        }

        a:hover {
            background-color: #464646;
            border-radius: 5px;
        }

        .gap-15 {
            gap: 15px;
        }
    }
}



.search-bar {
    input {
        border: none;
        width: 350px;
        line-height: 30px;
        margin: 0 10px;
        padding: 0 10px;
        color: white;
        border-radius: 5px;
        background-color: rgb(26, 25, 25);
    }

    input:hover {
        background-color: #464646;
        border-radius: 5px;
    }

    button {
        color: white;
        border: none;
        cursor: pointer;
        height: 35px;
        width: 80px;
        border-radius: 5px;
        background-color: rgb(26, 25, 25);
    }

    button:hover {
        background-color: #464646;
    }
}

@media (max-width: 1277px) {
    .display-none-md {
        display: none;
    }
    .header-bar{
        display: flex;
        flex-wrap: wrap;
    }
}
</style>
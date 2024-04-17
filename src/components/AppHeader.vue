<template>
    <div class="header-bar">
        <div class="row">
            <div class="logo">
                <h1>BOOLFLIX</h1>
            </div>
            <div class="vision-option">
                <ul class="row gap-15">
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Serie TV</a></li>
                    <li><a href="#">Film</a></li>
                    <li><a href="#">Originali</a></li>
                    <li><a href="#">Aggiunti di recente</a></li>
                    <li><a href="#">La mia lista</a></li>
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
.header-bar{
    margin: 20px 20px 40px 20px;
    align-items: center;
    .logo{
        margin-right: 40px;
        color: red
    };
    .vision-option{
        display: flex;
        align-items: center;
        a{
            text-decoration: none;
            color: white;
        }
        .gap-15{
            gap: 25px;
        }
    };
}
.search-bar {
    input{
        border: none;
        width: 350px;
        line-height: 30px;
        margin: 0 10px;
        color: white;
    }
    button{
        color: white;
        border: none;
        cursor: pointer;
        height: 35px;
        width: 80px;
        border-radius: 5px;
    }
    button:hover {
    background-color: #464646;
}
}
</style>
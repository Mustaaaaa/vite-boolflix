<template>
    <div class="search-bar">
        <input type="text" v-model="searchQuery" placeholder="Cerca un film o una Serie...">
        <button @click="search">Cerca</button>
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

</style>
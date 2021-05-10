<template>
    <div id="app">
        <Header @searchedText="updateSearch" />
        <Main :films="filmsArray" />
    </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
    name: "App",
    components: {
        Header,
        Main,
    },
    data() {
        return {
            filmsArray: [],
            filmsAPI: "https://api.themoviedb.org/3/search/movie",
        };
    },
    methods: {
        updateSearch(text) {
            axios
                .get(this.filmsAPI, {
                    params: {
                        api_key: "d1e4e847879a0dc2e8ffcc9d9faf5a8f",
                        query: text,
                        language: "it-IT",
                    },
                })
                .then((res) => {
                    this.filmsArray = res.data.results;
                    console.log(this.filmsArray);
                })
                .catch((err) => {
                    console.log(err);
                });
        },
    },
};
</script>

<style lang="scss">
@import "@/styles/general";
</style>

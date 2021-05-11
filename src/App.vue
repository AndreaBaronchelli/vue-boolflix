<template>
    <div id="app">
        <Header @searchedText="updateSearch" />
        <Main :films="filmsArray.concat(seriesArray)" />
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
            seriesArray: [],
            filmsArray: [],
            filmsAPI: "https://api.themoviedb.org/3/search/movie",
            seriesAPI: "https://api.themoviedb.org/3/search/tv",
            trandingAPI: "https://api.themoviedb.org/3/trending/all/week",
        };
    },
    created() {
        // GET TRANDING FILMS
        axios
            .get(this.trandingAPI, {
                params: {
                    api_key: "d1e4e847879a0dc2e8ffcc9d9faf5a8f",
                },
            })
            .then((res) => {
                this.filmsArray = res.data.results;
            })
            .catch((err) => {
                console.log(err);
            });
    },
    methods: {
        updateSearch(text) {
            // API CALL FILMS
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
                })
                .catch((err) => {
                    console.log(err);
                });

            // API CALL SERIES
            axios
                .get(this.seriesAPI, {
                    params: {
                        api_key: "d1e4e847879a0dc2e8ffcc9d9faf5a8f",
                        query: text,
                        language: "it-IT",
                    },
                })
                .then((res) => {
                    this.seriesArray = res.data.results;
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
#app {
    background-color: #1d1d1d;
}
</style>

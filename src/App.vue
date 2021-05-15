<template>
    <div id="app">
        <Header @searchedText="updateSearch" />

        <section class="Home" v-if="searchText == ''">
            <Home
                :tranding="trandigFilmArray"
                :trandingTV="trandigTvArray"
                :discover="discoverArray"
            />
        </section>

        <section class="search" v-else>
            <Search
                :films="filmsArray.concat(seriesArray)"
                :searchText="searchText"
            />
        </section>
    </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Search from "@/components/Search.vue";
import Home from "@/components/Home.vue";

export default {
    name: "App",
    components: {
        Header,
        Search,
        Home,
    },
    data() {
        return {
            seriesArray: [],
            filmsArray: [],
            trandigFilmArray: [],
            trandigTvArray: [],
            discoverArray: [],
            filmsAPI: "https://api.themoviedb.org/3/search/movie",
            seriesAPI: "https://api.themoviedb.org/3/search/tv",
            trandingMoviesAPI:
                "https://api.themoviedb.org/3/trending/movies/week",
            trandingTVAPI: "https://api.themoviedb.org/3/trending/tv/week",
            discoverAPI: "https://api.themoviedb.org/3/discover/movie",
            searchText: "",
        };
    },
    created() {
        // GET TRANDING FILMS
        axios
            .get(this.trandingMoviesAPI, {
                params: {
                    api_key: "d1e4e847879a0dc2e8ffcc9d9faf5a8f",
                },
            })
            .then((res) => {
                this.trandigFilmArray = res.data.results;
            })
            .catch((err) => {
                console.log(err);
            });

        // GET TRANDING TV SHOWS
        axios
            .get(this.trandingTVAPI, {
                params: {
                    api_key: "d1e4e847879a0dc2e8ffcc9d9faf5a8f",
                },
            })
            .then((res) => {
                this.trandigTvArray = res.data.results;
            })
            .catch((err) => {
                console.log(err);
            });

        // GET DISCOVER NEW MOVIES
        axios
            .get(this.discoverAPI, {
                params: {
                    api_key: "d1e4e847879a0dc2e8ffcc9d9faf5a8f",
                },
            })
            .then((res) => {
                this.discoverArray = res.data.results;
            })
            .catch((err) => {
                console.log(err);
            });
    },
    methods: {
        updateSearch(text) {
            // Update searchtext
            this.searchText = text;

            // Reset Search
            if (text == "") {
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
            }

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
    overflow: hidden;
    min-height: 100vh;
    background-color: #1d1d1d;
}
</style>

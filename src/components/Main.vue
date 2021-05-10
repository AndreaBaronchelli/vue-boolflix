<template>
    <main class="container">
        <Card v-for="item in filmsArray" :key="item.id" :info="item" />
        <button @click="getFilms">Click</button>
    </main>
</template>

<script>
import axios from "axios";
import Card from "@/components/Card.vue";

export default {
    name: "Main",
    components: {
        Card,
    },
    data() {
        return {
            filmsArray: [],
            filmsAPI: "https://api.themoviedb.org/3/search/movie",
        };
    },
    methods: {
        getFilms() {
            axios
                .get(this.filmsAPI, {
                    params: {
                        api_key: "d1e4e847879a0dc2e8ffcc9d9faf5a8f",
                        query: "ritorno al futuro",
                        language: "it-IT",
                    },
                })
                .then((res) => {
                    console.log(res.data.results);
                    this.filmsArray = res.data.results;
                })
                .catch((err) => {
                    console.log(err);
                });
        },
    },
};
</script>

<style scoped lang="scss">
@import "@/styles/utilities";

main {
    display: flex;
    flex-wrap: wrap;
}
</style>

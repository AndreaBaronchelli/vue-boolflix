<template>
    <div id="app">
        <Header @searchedText="updateSearch" />
        <Main :searchData="searchText" />
    </div>
</template>

<script>
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
            searchText: "",
        };
    },
    methods: {
        updateSearch(data) {
            this.searchText = data;
        },
    },
};
</script>

<style lang="scss">
@import "@/styles/general";
</style>

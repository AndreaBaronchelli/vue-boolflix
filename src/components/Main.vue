<template>
    <main class="container">
        <Card v-for="item in filteredArray" :key="item.id" :info="item" />
    </main>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
    name: "Main",
    components: {
        Card,
    },
    props: ["films"],
    data() {
        return {
            filmsArray: this.films,
        };
    },
    computed: {
        filteredArray() {
            return this.filmsArray;
        },
    },
    methods: {},
};
</script>

<style scoped lang="scss">
@import "@/styles/utilities";

main {
    display: flex;
    flex-wrap: wrap;
}
</style>

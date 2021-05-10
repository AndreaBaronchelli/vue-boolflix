<template>
    <main class="container">
        <Card v-for="item in filmsArray" :key="item.id" :info="item" />
        <button @click="test">test</button>
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

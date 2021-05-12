<template>
    <main class="container">
        <section class="search">
            <h2>Search for: "{{ searchText }}"</h2>
            <div class="cards">
                <Card v-for="item in films" :key="item.id" :info="item" />
            </div>
        </section>
    </main>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
    name: "Main",
    components: {
        Card,
    },
    props: {
        films: Array,
        searchText: String,
    },
    data() {
        return {};
    },
};
</script>

<style scoped lang="scss">
@import "@/styles/utilities";
@import "@/styles/vars";

main {
    padding-top: 110px;
    h2 {
        color: $brand-color;
        margin-bottom: 2rem;
    }
    .cards {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
}
</style>

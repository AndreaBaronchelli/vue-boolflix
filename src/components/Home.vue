<template>
    <main class="container">
        <section>
            <h2>Bests Movies of the Week</h2>
            <div class="cards">
                <Card v-for="item in tranding" :key="item.id" :info="item" />
            </div>
        </section>
        <section>
            <h2>Bests TV Shows the Week</h2>
            <div class="cards">
                <Card v-for="item in trandingTV" :key="item.id" :info="item" />
            </div>
        </section>
        <section>
            <h2>Discover New Movies</h2>
            <div class="cards">
                <Card v-for="item in discover" :key="item.id" :info="item" />
            </div>
        </section>
    </main>
</template>

<script>
import Card from "@/components/Card.vue";
export default {
    name: "Home",
    components: {
        Card,
    },
    props: {
        tranding: Array,
        trandingTV: Array,
        discover: Array,
    },
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/utilities";

main {
    padding-top: 110px;
    section {
        margin-bottom: 20px;
        h2 {
            margin-bottom: 2rem;
            color: $text-color;
        }
        .cards {
            display: flex;
            overflow-x: auto;
        }
    }
}
</style>

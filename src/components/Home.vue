<template>
    <main class="container">
        <section>
            <h2>TRENDING FILMS OF THE WEEK</h2>
            <div class="cards">
                <Card v-for="item in tranding" :key="item.id" :info="item" />
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
    },
};
</script>

<style scoped lang="scss">
@import "../styles/vars";
@import "../styles/utilities";

main {
    padding-top: 110px;
    h2 {
        margin-bottom: 2rem;
        color: $brand-color;
    }
    .cards {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
}
</style>

<template>
    <main class="container">
        <Card v-for="item in films" :key="item.id" :info="item" />
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
        return {};
    },
};
</script>

<style scoped lang="scss">
@import "@/styles/utilities";

main {
    display: flex;
    flex-wrap: wrap;
    padding-top: 100px;
}
</style>

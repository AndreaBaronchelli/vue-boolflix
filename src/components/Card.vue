<template>
    <div class="card">
        <ul>
            <li>Titolo: {{ info.title }}</li>
            <li>Titolo Originale: {{ info.original_title }}</li>
            <li>Lingua Originale: {{ info.original_language }}</li>
            <li>Voto: {{ info.vote_average }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: ["info"],
};
</script>

<style scoped lang="scss">
.card {
    margin-right: 50px;
}
</style>

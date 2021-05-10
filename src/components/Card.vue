<template>
    <div class="card">
        <ul>
            <li>Titolo: {{ info.title }}</li>
            <li>Titolo Originale: {{ info.original_title }}</li>
            <li v-if="!flagsArray.includes(info.original_language)">
                Lingua Originale: {{ info.original_language }}
            </li>
            <li v-else>
                <span>Lingua Originale:</span>
                <img
                    :src="
                        require(`../assets/img/${info.original_language}.png`)
                    "
                    alt=""
                />
            </li>
            <li>Voto: {{ info.vote_average }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: ["info"],
    data() {
        return {
            flagsArray: ["en", "it"],
        };
    },
};
</script>

<style scoped lang="scss">
.card {
    width: 300px;
    margin-right: 50px;
    margin-bottom: 50px;
    img {
        width: 20px;
        margin-left: 5px;
    }
}
</style>

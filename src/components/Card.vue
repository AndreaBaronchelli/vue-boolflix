<template>
    <div class="card">
        <ul>
            <li>Titolo: {{ info.title == null ? info.name : info.title }}</li>
            <li>
                Titolo Originale:
                {{
                    info.original_title == null
                        ? info.original_name
                        : info.original_title
                }}
            </li>
            <li v-if="!flagsArray.includes(info.original_language)">
                Lingua Originale: {{ info.original_language }}
            </li>
            <li class="language" v-else>
                <span>Lingua Originale:</span>
                <img
                    :src="
                        require(`../assets/img/${info.original_language}.png`)
                    "
                    alt=""
                />
            </li>
            <li>
                Voto:
                <span
                    v-for="(star, index) in Math.ceil(info.vote_average / 2)"
                    :key="index"
                >
                    <i class="fa fa-star"></i
                ></span>
                <!-- <span
                    v-for="(star, index) in Math.ceil(
                        6 - info.vote_average / 2
                    )"
                    :key="index"
                >
                    <i class="fa fa-star"></i
                ></span> -->
            </li>
            <li>
                <img
                    :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`"
                    alt=""
                />
            </li>
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
    methods: {
        getStars(vote) {
            // Convert vote
            let stars = Math.round(vote / 2);
            console.log(stars);
        },
    },
};
</script>

<style scoped lang="scss">
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css";

.card {
    width: 300px;
    margin-right: 50px;
    margin-bottom: 50px;
    .language {
        img {
            width: 20px;
        }
    }
    img {
        max-width: 250px;
    }
}
</style>

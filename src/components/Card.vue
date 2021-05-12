<template>
    <div class="card">
        <img
            v-if="info.poster_path !== null"
            class="poster"
            :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`"
            alt=""
        />
        <img
            v-else
            class="poster not-found"
            src="../assets/img/not_found.png"
            alt=""
        />
        <ul>
            <li>
                <strong>Titolo:</strong>
                {{ info.title == null ? info.name : info.title }}
            </li>
            <li>
                <strong>Titolo Originale:</strong>
                {{
                    info.original_title == null
                        ? info.original_name
                        : info.original_title
                }}
            </li>
            <li v-if="!flagsArray.includes(info.original_language)">
                <strong>Lingua Originale:</strong> {{ info.original_language }}
            </li>
            <li class="language" v-else>
                <strong>Lingua Originale:</strong>
                <img
                    :src="
                        require(`../assets/img/${info.original_language}.png`)
                    "
                    alt=""
                />
            </li>
            <li>
                <strong>Voto:</strong>
                <span
                    v-for="(star, i) in Math.ceil(info.vote_average / 2)"
                    :key="i"
                >
                    <i class="fa fa-star full"></i
                ></span>
                <span
                    v-for="(star, i) in 5 - Math.ceil(info.vote_average / 2)"
                    :key="'A' + i"
                >
                    <i class="fa fa-star"></i
                ></span>
            </li>
            <li class="overview"><strong>Info: </strong>{{ info.overview }}</li>
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
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css";
@import "../styles/vars.scss";

.card {
    position: relative;
    width: 340px;
    min-height: 500px;
    margin-right: 10px;
    margin-bottom: 20px;
    overflow: hidden;
    cursor: pointer;
    .poster {
        position: absolute;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
    }
    ul {
        z-index: 1;
        position: absolute;
        top: 50%;
        left: 1rem;
        transform: translateY(-50%);
        list-style: none;
        color: $text-color;
        opacity: 0;
        transition: opacity 0.4s;
    }
    li {
        margin-bottom: 1rem;
        i {
            margin-left: 5px;
        }
        .full {
            color: rgb(214, 190, 80);
        }
    }
    .language {
        img {
            width: 1.5rem;
            margin-left: 5px;
        }
    }
    .overview {
        max-height: 10rem;
        margin-bottom: 1rem;
        overflow: hidden;
        text-overflow: ellipsis;
    }
}

// LAYOVER
.card::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background-color: rgba(#000, 0.8);
    opacity: 0;
    transition: opacity 0.4s;
}

.card:hover::after,
.card:hover ul {
    opacity: 1;
}
</style>

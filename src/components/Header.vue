<template>
    <header>
        <div class="container">
            <div class="logo">
                <a href="#">
                    <img
                        src="../assets/img/0b68cfd2bef3757aeb2259bad9581728.png"
                        alt="BaronFlix Logo"
                    />
                </a>
            </div>
            <input
                type="text"
                placeholder="Cerca i tuoi film e serie tv preferite..."
                v-model.trim="searchText"
                @keyup="$emit('searchedText', searchText)"
            />
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            searchText: "",
        };
    },
};
</script>

<style scoped lang="scss">
@import "@/styles/utilities";
@import "../styles/vars";
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css";

header {
    z-index: 2;
    position: fixed;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-top: 1rem;
    }
    img {
        height: 70px;
    }
    input {
        outline: none;
        border: 1px solid transparent;
        border-radius: 10px;
        width: 250px;
        height: 40px;
        padding: 0.5rem;
        color: $text-color;
        background-color: #1d1d1d;
        transition: width 0.3s;
    }
    input:hover,
    input:focus {
        width: 400px;
    }
}
</style>

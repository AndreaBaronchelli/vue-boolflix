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
            <form>
                <input
                    type="text"
                    placeholder="Cerca i tuoi film e serie tv preferite..."
                    v-model.trim="searchText"
                />
                <button
                    type="submit"
                    @click.prevent="$emit('searchedText', searchText)"
                >
                    CERCA
                </button>
            </form>
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
    form {
        width: 40%;
        display: flex;
        input {
            outline: none;
            flex-grow: 1;
            margin-right: 20px;
            height: 40px;
            padding: 0.5rem;
        }
        button {
            height: 40px;
            padding: 0 2rem;
            border: 1px solid transparent;
            border-radius: 10px;
            color: $text-color;
            background-color: $brand-color;
            cursor: pointer;
        }
    }
}
</style>

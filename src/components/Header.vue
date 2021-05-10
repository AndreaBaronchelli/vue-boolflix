<template>
    <header class="container">
        <div class="logo">
            <img
                src="../assets/img/0b68cfd2bef3757aeb2259bad9581728.png"
                alt="BaronFlix Logo"
            />
        </div>
        <form>
            <input
                type="text"
                placeholder="Cerca i tuoi film e serie tv preferite..."
                v-model="searchText"
            />
            <button
                type="submit"
                @click.prevent="$emit('searchText', searchText)"
            >
                Cerca
            </button>
        </form>
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

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 1rem;
    img {
        height: 70px;
    }
    form {
        width: 40%;
        display: flex;
        input {
            flex-grow: 1;
            margin-right: 20px;
        }
    }
}
</style>

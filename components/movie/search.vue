<script setup>
const query = ref("batman");
const movies = ref([]);

const search = async () => {
    const {Search} = await $fetch(`http://www.omdbapi.com/?apikey=e12106f3&s=${query.value}`);
    movies.value = Search;
}

search();
</script>
<template>
    <div>
        <form @submit.prevent="search">
            <input type="search" v-model="query" />
            <button>Search</button>
        </form>

        <ul style="display: flex; flex-wrap: wrap; gap: 10px; list-style: none">
            <li v-for="movie in movies" :key="movies.imdbID">
                <nuxt-link :to="{ name: 'movies-id', params: {id: movie.imdbID} }">
                    <img :src="movie.Poster" :alt="movie.Title" />
                </nuxt-link>
            </li>
        </ul>
    </div>
</template>

<style scoped></style>

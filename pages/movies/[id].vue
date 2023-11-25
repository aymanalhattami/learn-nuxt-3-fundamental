<script setup>
    import {useAsyncData} from "#app";
    const route = useRoute();

    const { data } = await useFetch(`http://www.omdbapi.com/?apikey=e12106f3&i=${route.params.id}`, {
        pick: ['Plot', 'Title', 'Poster', 'Error'],
        key: `/movies/${route.params.id}`
    });

    console.log(data);

    if(data.value.Error === "Incorrect IMDb ID."){
        showError({statusCode: 404, statusMessage: 'Movie not found'} );
    }

    useHead({
        'title': data.value.Title,
        meta: [
            {name: "description", content: data.value.Plot},
            {property: "og:description", content: data.value.Plot},
            {property: "og:image", content: data.value.Poster},
            {name: 'twitter:card', content: 'summary_large_image'}
        ]
    })

    // const { data } = useAsyncData(`/movies/${route.params.id}`, () => {
    //     return $fetch(`http://www.omdbapi.com/?apikey=e12106f3&i=${route.params.id}`);
    // }, {
    //     pick: ['Plot', 'Title']
    // })
</script>

<template>
    <pre>
        {{ data }}
    </pre>
</template>

<style scoped>

</style>
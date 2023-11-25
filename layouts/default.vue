<script setup lang="ts">
// const isLoggedIn = useIsLoggedIn();
const user = useUser();
</script>

<template>
    <nav>
        <NuxtLink to="/">Home</NuxtLink> |
        <NuxtLink to="/movies">Movies</NuxtLink> |
        <NuxtLink to="/admin">Admin</NuxtLink> |
        <NuxtLink v-if="!user.isLoggedIn" to="/login">Login</NuxtLink>
        <a href="#" @click.prevent="user.isLoggedIn = false" v-else >Logout</a>
    </nav>

    <slot></slot>
</template>

<style scoped>

</style>
<script setup>
const user = useUser();
definePageMeta({
    layout: 'plain'
})

const login = () => {
    user.isLoggedIn = true;

    useRouter().push('/');
}
</script>

<template>
<div>
    <h1>Login</h1>
    <button @click.prevent="login">login</button>
</div>
</template>

<style scoped>

</style>
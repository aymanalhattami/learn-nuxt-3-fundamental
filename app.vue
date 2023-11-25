<script setup>
useHead({
    titleTemplate: (titleChunk) => {
        return titleChunk ? `My Movies | ${titleChunk}` : 'My Movies';
    }
})
</script>

<template>
  <div>
      <NuxtLayout>
        <nuxt-page />
      </NuxtLayout>
  </div>
</template>

<template>
    <div class="container">
      <v-btn
            elevation="2"
            rounded
            to="/"
        >To main page</v-btn>
        <v-img
        max-width="600"
        :src="catUrl"
        ></v-img>
    </div>
</template>

<script>
export default {
  async asyncData({ $route, $axios }) {
    const id = $nuxt.$route.params.id
    const catImg = await $axios.$get(`https://cataas.com/cat/sad/says/hello?json=true&size=${id}&color=blue`)
    const catUrl = `https://cataas.com${catImg.url}`
    return {catUrl}
  }
}
</script>
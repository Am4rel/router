<template>
    <div class="container">
      <v-list-item-group>
                  
                    <v-list>
                      <v-list-item-content>
                        <NuxtLink :to="linkBlue">Sad cat says hello, width {{id}}, color blue</NuxtLink>
                      </v-list-item-content>
                    </v-list>
                    <v-list-item>
                      <v-list-item-content>
                        <NuxtLink :to="linkRed">Sad cat says hello, width {{id}}, color red</NuxtLink>
                      </v-list-item-content>
                    </v-list-item>

            </v-list-item-group>     
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
  data() {
    return {
      id: $nuxt.$route.params.id,
      linkBlue: `/sad/hello/${$nuxt.$route.params.id}/blue`,
      linkRed: `/sad/hello/${$nuxt.$route.params.id}/red`
    }
  },
  async asyncData({ $axios }) {
    const id = $nuxt.$route.params.id
    const catImg = await $axios.$get(`https://cataas.com/cat/sad/says/hello?json=true&size=${id}`)
    const catUrl = `https://cataas.com${catImg.url}`
    return {catUrl}
  }
}
</script>
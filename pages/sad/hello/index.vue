<template>
    <div class="container">
      <v-list-item-group>

        <v-list-item>
          <v-list-item-content>
            <NuxtLink to="/sad/hello/my_fellow_kids">Sad cat says hello my fellow kids</NuxtLink>
          </v-list-item-content>
        </v-list-item>

        <v-list-item>
          <v-list-item-content>
            <NuxtLink to="/sad/hello/600">Sad cat says hello, width 600</NuxtLink>
          </v-list-item-content>
        </v-list-item>

        <v-list-item>
          <v-list-item-content>
            <NuxtLink to="/sad/hello/300">Sad cat says hello, width 300</NuxtLink>
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
  async asyncData({ $axios }) {
    const catImg = await $axios.$get('https://cataas.com/cat/sad/says/hello?json=true')
    const catUrl = `https://cataas.com${catImg.url}`
    return {catUrl}
  }
}
</script>
<template>
  <div class="container">
      <v-list-item-group>    
            <v-list-item-content>
              <NuxtLink to="/sad">Sad cats</NuxtLink>
            </v-list-item-content>
          
            <v-list-item-content>
              <NuxtLink to="/cute">Cute cats</NuxtLink>
            </v-list-item-content>

      </v-list-item-group>

      <v-card
        elevation="10"
        width="600px"
      >
      <v-card-title>
        Simple router homework
      </v-card-title>
    <v-card-text>
      I added an API that shows you random images with cats, each route calls it with different paraneters and returns new cat.
    </v-card-text>
  </v-card>

    <NuxtChild class="container"/>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const catImg = await $axios.$get('https://cataas.com/cat?json=true')
    const catUrl = `https://cataas.com${catImg.url}`
    console.log($nuxt.$route.name)
    return {catUrl}
  }
}
</script>

<style>
.container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.v-btn {
  margin: 20px 0;
}

.v-item-group {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, max-content));
  justify-items: center;
}

.v-card {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;

  text-align: center;
  margin-top: 50px;
}
</style>
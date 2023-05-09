<template>
  <v-banner shaped tile>
    <v-img :src="`https://image.tmdb.org/t/p/w500${data.poster_path}`"></v-img>
    <v-btn
      color="success"
      width="100px"
      block
      depressed
      class="white--text mt-3"
      style="overflow: hidden"
      :to="`/watchPage/${data.id}`"
      nuxt
    >
      <v-icon>mdi-arrow-right-drop-circle-outline</v-icon>
      Watch Movie
    </v-btn>
    <v-btn
      color="error"
      width="100px"
      block
      depressed
      class="white--text mt-3"
      style="overflow: hidden"
      :to="`/watchPage/${data.id}`"
      nuxt
    >
      <v-icon>mdi-arrow-right-drop-circle-outline</v-icon>
      Watch Trailer
    </v-btn>
  </v-banner>
</template>

<script>
export default {
  props: {
    // eslint-disable-next-line vue/require-default-prop
    data: {
      type: Object,
    },
  },
}
</script>

<style></style>

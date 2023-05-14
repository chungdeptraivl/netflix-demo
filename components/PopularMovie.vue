<template>
  <v-card class="card-container" :to="`/moviePage/${movie.id}`" nuxt>
    <v-img :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`" cover>
      <template #placeholder>
        <v-row class="fill-height ma-0" align="center" justify="center">
          <v-progress-circular
            indeterminate
            color="grey-lighten-5"
          ></v-progress-circular>
        </v-row>
      </template>
    </v-img>
    <v-card-title class="card-title">{{ movie.title }} </v-card-title>
  </v-card>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style scoped>
.card-title {
  width: 100%;
  height: 100px;
  overflow: hidden;
  padding: 10px;
  font-size: 18px;
  font-weight: bold;
  white-space: nowrap;
  background-color: #212121;
  color: #e50914;
}
</style>

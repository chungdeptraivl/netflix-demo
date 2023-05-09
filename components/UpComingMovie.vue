<template>
  <v-card class="card-container ma-5" height="300" width="200" :to="`/moviePage/${item.id}`" nuxt>
    <v-img
      height="100%"
      :src="`https://image.tmdb.org/t/p/w500${item.poster_path}`"
    >
  </v-img>
  <v-card-title class="card-title">{{ item.title }} </v-card-title>

    <div class="d-flex fill-height align-center justify-center">
      <v-scale-transition>
        <v-icon
          color="white"
          size="80px"
          icon="mdi-close-circle-outline"
        ></v-icon>
      </v-scale-transition>
    </div>
  </v-card>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style scoped>
  .card-title {
  position: relative;
  cursor: pointer;
}

.card-title {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  padding: 16px;
  color: #fff;
  background-color: rgba(0, 0, 0, 0.5);
  font-weight: 500;
  text-align: center;
  transform: translateY(100%);
  transition: transform 0.3s ease-in-out;
}

.card-container:hover .card-title {
  transform: translateY(0);
}
</style>

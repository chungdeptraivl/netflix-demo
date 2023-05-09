<template>
  <v-sheet height="100%">
    <div class="d-flex fill-height justify-center align-center">
      <v-img
        width="100%"
        :src="`https://image.tmdb.org/t/p/w500${item.backdrop_path}`"
      ></v-img>
    </div>
  </v-sheet>
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

<style scoped></style>

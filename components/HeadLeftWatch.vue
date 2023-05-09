<template>
    <v-banner shaped tile>
      <v-img :src="`https://image.tmdb.org/t/p/w500${data.poster_path}`"></v-img>
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
  
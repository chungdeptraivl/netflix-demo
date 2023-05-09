<template>
  <div
    style="
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      flex-direction: column;
    "
  >
    <h1 style="color: #fff; margin: 10px 0 10px 0">
      {{ data.original_title }}
    </h1>
    <p style="color: #ba0c15; font-weight: bold">
      Genres:
      <v-btn
        v-for="(genre, i) in data.genres"
        :key="i"
        color="primary"
        style="margin: 0 10px"
        size="x-small"
        >{{ genre.name }}
      </v-btn>
    </p>
    <p style="color: #ba0c15; font-weight: bold">
      Director:
      <span
        v-for="(d, i) in getDirector"
        :key="i"
        style="color: #fff; font-weight: bold"
      >
        {{ d }}
        <span v-if="getDirector.length - 1 != i">, </span>
      </span>
    </p>
    <p style="color: #ba0c15; font-weight: bold">
      Release date:
      <span style="color: #fff">{{
        new Date(data.release_date).toLocaleString('en-us', {
          day: 'numeric',
          month: 'long',
          year: 'numeric',
        })
      }}</span>
    </p>
    <p style="color: #ba0c15; font-weight: bold">
      Runtime:
      <span style="color: #fff"> {{ data.runtime }} min</span>
    </p>
    <p style="color: #ba0c15; font-weight: bold">
      Description:
      <span style="color: #fff"> {{ data.overview }}</span>
    </p>

    <rating-movie :data="data" />
  </div>
</template>

<script>
import RatingMovie from './RatingMovie.vue'
export default {
  components: { RatingMovie },

  props: {
    // eslint-disable-next-line vue/require-default-prop
    data: {
      type: Object,
    },
  },

  computed: {
    getDirector() {
      const directors = []
      for (const item of this.data.credits.crew) {
        if (item.job === 'Director') {
          directors.push(item.name)
        }
      }
      return directors
    },
  },
}
</script>

<style></style>

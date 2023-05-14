<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="3">
        <head-left-watch :data="data" />
      </v-col>
      <v-col cols="12" sm="9">
        <head-middle-watch :data="data" />
      </v-col>
    </v-row>
    <hr />
    <watch-movie-page :data="data" />
    <hr />

    <!-- Recommend movie -->
    <div class="mt-4">
      <h2 style="color: #fff">Recommend Movie</h2>
      <v-slide-group multiple show-arrows="">
        <v-slide-item
          v-for="movie in recommendations"
          :key="movie.id"
          v-slot="{ toggle }"
        >
          <v-card
            class="ma-4"
            :to="`/moviePage/${movie.id}`"
            nuxt
            @click="toggle"
          >
            <v-img
              cover
              width="100"
              height="160"
              :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`"
            ></v-img>
          </v-card>
        </v-slide-item>
      </v-slide-group>
    </div>
  </v-container>
</template>

<script>
import HeadLeftWatch from '~/components/HeadLeftWatch.vue'
import HeadMiddleWatch from '~/components/HeadMiddleWatch.vue'
import WatchMoviePage from '~/components/WatchMoviePage.vue'

export default {
  components: { HeadLeftWatch, HeadMiddleWatch, WatchMoviePage },
  async asyncData({ params, $axios }) {
    try {
      const result = await $axios.$get(
        `/movie/${params.id}?append_to_response=credits,videos,images`
      )

      const result2 = await $axios.$get(`/movie/${params.id}/recommendations`)

      // eslint-disable-next-line no-console
      console.log(result)

      return {
        data: result,
        recommendations: result2.results.slice(0, 15)
      }
    } catch (error) {
      // eslint-disable-next-line no-console
      console.log('co loi')
    }
  },
}
</script>

<style></style>

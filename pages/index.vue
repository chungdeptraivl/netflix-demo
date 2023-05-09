<template>
  <div>
    <!-- Now Playing Movies -->
    <v-carousel cycle height="100%" hide-delimiter-background>
      <v-carousel-item v-for="item in nowPlayingMovies" :key="item.id">
        <now-playing-movie :item="item" />
      </v-carousel-item>
    </v-carousel>
    <v-container class="mb-5">
      <!-- Top Rate Movies -->
      <nuxt-link to="/movies" style="text-decoration: none">
        <v-btn block dark class="mt-5 mb-2">
          <h1>Top Rate Movies</h1>
        </v-btn>
      </nuxt-link>
      <hr class="mb-5" />
      <v-sheet
        v-if="topRateMovies.length"
        dark
        class="mx-auto"
        elevation="8"
        max-width="100%"
      >
        <v-slide-group class="pa-4" center-active show-arrows>
          <v-slide-group-item v-for="item in topRateMovies" :key="item.id">
            <top-rate-movie :item="item" />
          </v-slide-group-item>
        </v-slide-group>
      </v-sheet>

      <!-- Up Coming Movies -->
      <nuxt-link to="/movies" style="text-decoration: none">
        <v-btn block dark class="mt-5 mb-2">
          <h1>Up Coming Movies</h1>
        </v-btn>
      </nuxt-link>
      <hr class="mb-5" />
      <v-sheet
        v-if="upComingMovies.length"
        dark
        class="mx-auto"
        elevation="8"
        max-width="100%"
      >
        <v-slide-group class="pa-4" center-active show-arrows>
          <v-slide-group-item v-for="item in upComingMovies" :key="item.id">
            <up-coming-movie :item="item" />
          </v-slide-group-item>
        </v-slide-group>
      </v-sheet>

      <!-- Popular Movies -->
      <nuxt-link to="/movies" style="text-decoration: none">
        <v-btn block dark class="mt-5 mb-2">
          <h1>Popular Movies</h1>
        </v-btn>
      </nuxt-link>
      <hr class="mb-5" />
      <v-row v-if="popularMovies.length">
        <v-col
          v-for="movie in popularMovies"
          :key="movie.id"
          cols="12"
          sm="4"
          xs="6"
          md="3"
          lg="3"
        >
          <popular-movie :movie="movie" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import NowPlayingMovie from '~/components/NowPlayingMovie.vue'
import TopRateMovie from '~/components/TopRateMovie.vue'
import UpComingMovie from '~/components/UpComingMovie.vue'
import PopularMovie from '~/components/PopularMovie.vue'

export default {
  name: 'IndexPage',
  components: { PopularMovie, UpComingMovie, NowPlayingMovie, TopRateMovie },

  async asyncData({ $axios }) {
    try {
      const nowPlayingMovies = await $axios.$get('/movie/now_playing')
      const topRateMovies = await $axios.$get('/movie/top_rated')
      const upComingMovies = await $axios.$get('/movie/upcoming')
      const popularMovies = await $axios.$get('/movie/popular')

      // eslint-disable-next-line no-console
      console.log(nowPlayingMovies)
      // eslint-disable-next-line no-console
      console.log(upComingMovies)
      // eslint-disable-next-line no-console
      console.log(topRateMovies)
      // eslint-disable-next-line no-console
      console.log(popularMovies)

      return {
        nowPlayingMovies: nowPlayingMovies.results.slice(0, 5),
        upComingMovies: upComingMovies.results.slice(0, 15),
        topRateMovies: topRateMovies.results.slice(0, 15),
        popularMovies: popularMovies.results.slice(0, 20),
      }
    } catch (error) {
      // eslint-disable-next-line no-console
      console.log('no movie')
    }
  },
}
</script>

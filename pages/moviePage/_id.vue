<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="3">
        <left-movie-info :data="data" />
      </v-col>
      <v-col cols="12" sm="9">
        <middle-movie-info :data="data" />
        <hr />

        <!-- ImageMovies -->
        <div class="mt-4">
          <h2 style="color: #fff">Images Movie</h2>
          <v-slide-group multiple show-arrows="">
            <v-slide-item
              v-for="(image, index) in data.images.backdrops"
              :key="index"
              v-slot="{ toggle }"
            >
              <v-card class="ma-4" @click="toggle">
                <v-img
                  cover
                  width="100"
                  height="160"
                  :src="`https://image.tmdb.org/t/p/w500${image.file_path}`"
                ></v-img>
              </v-card>
            </v-slide-item>
          </v-slide-group>
        </div>
        <hr />

        <!-- ActorMovies -->
        <div class="mt-4">
          <h2 style="color: #fff">Actors Movie</h2>
          <v-slide-group multiple show-arrows="">
            <v-slide-item
              v-for="(actor, index) in data.credits.cast"
              :key="index"
              v-slot="{ toggle }"
            >
              <v-card
                class="ma-4"
                :to="`/personPage/${actor.id}`"
                nuxt
                @click="toggle"
              >
                <v-img
                  cover
                  width="100"
                  height="160"
                  :src="`https://image.tmdb.org/t/p/w500${actor.profile_path}`"
                ></v-img>
              </v-card>
            </v-slide-item>
          </v-slide-group>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import LeftMovieInfo from '~/components/LeftMovieInfo.vue'
import MiddleMovieInfo from '~/components/MiddleMovieInfo.vue'
export default {
  components: { LeftMovieInfo, MiddleMovieInfo },

  async asyncData({ params, $axios }) {
    try {
      const result = await $axios.$get(
        `/movie/${params.id}?append_to_response=credits,videos,images`
      )
      // eslint-disable-next-line no-console
      console.log(result)

      return {
        data: result,
      }
    } catch (error) {
      // eslint-disable-next-line no-console
      console.log('co loi')
    }
  },
}
</script>

<style></style>

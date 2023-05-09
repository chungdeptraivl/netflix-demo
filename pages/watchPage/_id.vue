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
    <hr>
      <watch-movie-page :data="data" />
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
      // eslint-disable-next-line no-console
      console.log(result)

      return {
        data: result,
      }
    } catch (error) {
      // eslint-disable-next-line no-console
      console.log('co loi')
    }
  }
}
</script>

<style></style>

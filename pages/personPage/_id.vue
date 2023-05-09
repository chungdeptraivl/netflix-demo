<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="3">
        <left-person-info :data="data" />
      </v-col>
      <v-col cols="12" sm="9">
        <middle-person-info :data="data" />
        <hr />

        <!-- Actor's Movies -->
        <div class="mt-4">
          <h2 style="color: #fff">Actor's Movie</h2>
          <v-slide-group multiple show-arrows="">
            <v-slide-item
              v-for="(actor, index) in data.credits.cast"
              :key="index"
              v-slot="{ toggle }"
            >
              <v-card
                class="ma-4"
                :to="`/moviePage/${actor.id}`"
                nuxt
                @click="toggle"
              >
                <v-img
                  cover
                  width="100"
                  height="160"
                  :src="`https://image.tmdb.org/t/p/w500${actor.poster_path}`"
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
import LeftPersonInfo from '~/components/LeftPersonInfo.vue'
import MiddlePersonInfo from '~/components/MiddlePersonInfo.vue'

export default {
  components: { LeftPersonInfo, MiddlePersonInfo },

  async asyncData({ params, $axios }) {
    try {
      const result = await $axios.$get(
        `/person/${params.id}?append_to_response=credits,videos,images`
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
x
<style></style>

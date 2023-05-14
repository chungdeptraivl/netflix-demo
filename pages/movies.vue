<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col class="mx-4" cols="auto">
        <v-btn
          value="popular"
          density="comfortable"
          @click="handleGetBy('popular')"
          >Popular Movies</v-btn
        >
      </v-col>
      <v-col class="mx-4" cols="auto">
        <v-btn
          value="top_rated"
          density="comfortable"
          @click="handleGetBy('top_rated')"
          >Top Rate Movies</v-btn
        >
      </v-col>
      <v-col class="mx-4" cols="auto">
        <v-btn
          value="upcoming"
          density="comfortable"
          @click="handleGetBy('upcoming')"
          >Upcoming Movies</v-btn
        >
      </v-col>
    </v-row>
    <hr class="my-4" />
    <v-row>
      <v-col
        v-for="movie in movies"
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
    <v-row>
      <v-col cols="12">
        <div class="text-center">
          <v-pagination
            v-model="currentPage"
            :total-visible="8"
            :length="totalPages"
            @input="handlePage"
          >
          </v-pagination>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import PopularMovie from '~/components/PopularMovie.vue'
export default {
  components: { PopularMovie },
  data() {
    return {
      movies: [],
      getBy: 'popular',
      totalResults: 1,
      totalPages: 1,
      currentPage:
        parseInt(this.$route.query.page) > 1
          ? parseInt(this.$route.query.page)
          : 1,
    }
  },

  async fetch() {
    await this.$axios
      .$get(`/movie/${this.getBy}?page=${this.currentPage}`)
      .then((reponse) => {
        this.movies = reponse.results

        // eslint-disable-next-line no-console
        console.log(this.movies)
        this.totalPages = reponse.total_pages
        this.totalResults = reponse.total_results
        this.$router.push({ query: { page: this.currentPage } })
      })
  },

  methods: {
    handlePage(value) {
      this.currentPage = value
      this.$fetch()
    },
    handleGetBy(value) {
      this.getBy = value
      this.$fetch()
    },
  },
}
</script>

<style></style>

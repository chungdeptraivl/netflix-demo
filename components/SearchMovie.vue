<template>
  <div style="max-width: 350px">
    <v-text-field
      v-model="searchInput"
      append-icon="mdi-magnify"
      placeholder="Search Movies"
      single-line
      hide-details
      clearable
      dark
      style="width: 100%"
      @input="debounceSearch()"
      @keydown.enter="searchMovies()"
    >
    </v-text-field>

    <v-expand-transition v-if="loading">
      <p>Searching .....</p>
    </v-expand-transition>

    <v-expand-transition v-else-if="!results.length && searchInput">
      <p color="warning">No Having Movie'name</p>
    </v-expand-transition>

    <v-expand-x-transition v-else>
      <v-list color="transparent">
        <v-list-item
          v-for="item in results"
          :key="item.id"
          :to="`/moviePage/${item.id}`"
          nuxt
        >
          <v-list-item-avatar>
            <v-img
              :src="
                item.poster_path
                  ? `https://image.tmdb.org/t/p/w300${item.poster_path}`
                  : ''
              "
            ></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-expand-x-transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchInput: '',
      results: [],
      loading: false,
      debounce: null,
    }
  },

  methods: {
    debounceSearch() {
      if (this.debounce) clearTimeout(this.debounce)

      this.debounce = setTimeout(() => {
        this.getResults(this.searchInput)
      }, 500)
    },

    async getResults(query) {
      if (!query) {
        this.results = []
        this.loading = false
      }
      try {
        this.loading = true

        const response = await this.$axios.get(`/search/movie?query=${query}`)
        this.results = response.data.results.slice(0, 10)
        this.loading = false

        // eslint-disable-next-line no-console
        console.log(response)
        return false
      } catch (error) {
        // eslint-disable-next-line no-console
        console.log(error)
        this.loading = false
      }
    },

    searchMovies() {
      if (this.searchInput) {
        this.$router.push({
          name: 'searchPage-id',
          params: {
            id: this.searchInput,
          },
        })
      }
    },
  },
}
</script>

<style scoped></style>

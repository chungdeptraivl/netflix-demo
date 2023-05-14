<template>
  <v-app>
    <!-- Navbar -->
    <navbar-layout />

    <v-main style="background-color: #212121">
      <Nuxt />
    </v-main>

    <!-- Footer -->
    <footer-layout />

    <v-overlay :value="overlay" dark opacity="0.95">
      <search-movie />
      <v-btn v-if="overlay" class="closeOverlay" @click="overlay = false"
        >Close</v-btn
      >
    </v-overlay>
  </v-app>
</template>

<script>
import SearchMovie from '~/components/SearchMovie.vue'
export default {
  name: 'DefaultLayout',
  components: { SearchMovie },

  data() {
    return {
      overlay: false,
    }
  },

  watch: {
    $route(to, from) {
      this.overlay = false
    },
  },

  created() {
    this.$nuxt.$on('openOverlay', ($event) => (this.overlay = $event))
  },
}
</script>

<style scoped>
.closeOverlay {
  margin-top: 10px;
  color: #e50914;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  cursor: pointer;
}
</style>

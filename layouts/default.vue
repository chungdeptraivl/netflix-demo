<template>
  <v-app>
    <!-- Navbar -->
    <navbar-layout />

    <v-main style="background-color: #212121;">
      <Nuxt />
    </v-main>

    <!-- Footer -->
    <footer-layout />
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
}
</script>

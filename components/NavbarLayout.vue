<template>
  <div>
    <v-toolbar color="#212121">
      <v-toolbar-title style="cursor: pointer" @click="$router.push('/')">
        <h2
          style="
            font-size: 1.6rem;
            font-weight: 800;
            font-family: 'Netflix Sans', 'Helvetica Neue', Helvetica, Arial,
              sans-serif;
            color: #e50914;
            letter-spacing: -0.05em;
            text-shadow: rgba(0, 0, 0, 0.5) 0px 0px 10px;
          "
        >
          CHUNGFLIX
        </h2>
      </v-toolbar-title>

      <v-spacer />
      <v-text-field
        append-icon="mdi-magnify"
        placeholder="Search Movies"
        single-line
        hide-details
        clearable
        dark
        style="width: 100px"
        @click="$nuxt.$emit('openOverlay', true)"
      >
      </v-text-field>

      <v-spacer />
      <v-toolbar-items class="d-none d-md-flex">
        <v-btn
          v-for="(item, index) in items"
          :key="index"
          color="#fff"
          text
          link
          :to="item.link"
          >{{ item.title }}</v-btn
        >
      </v-toolbar-items>
      <span class="hidden-md-and-up">
        <v-app-bar-nav-icon
          color="#e50914"
          @click="drawer = true"
        ></v-app-bar-nav-icon>
      </span>
    </v-toolbar>
    <v-navigation-drawer v-model="drawer" absolute temporary left color="#333">
      <v-list dense nav>
        <v-list-item
          v-for="(item, index) in items"
          :key="index"
          :to="item.link"
          link
        >
          <v-list-item-content>
            <v-list-item-title style="color: #e50914">
              {{ item.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      items: [
        { title: 'Home', link: '/' },
        { title: 'Movies', link: '/movies' },
        { title: 'Movie Genre', link: '/genre' },
        { title: 'My Profile', link: '/profileUser' },
      ],
    }
  },
}
</script>

<style scoped></style>

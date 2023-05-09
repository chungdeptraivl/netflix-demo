<template>
  <div>
    <v-toolbar color="#212121">
      <v-toolbar-title style="margin-right: 4rem">
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
      <v-toolbar-items>
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
    </v-toolbar>
  </div>
</template>

<script>
export default {
  data() {
    return {
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

<style></style>

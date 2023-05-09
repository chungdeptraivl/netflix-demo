<template>
  <v-footer dark padless class="p-4 text-center d-flex flex-column">
    <div>
      <v-btn
        v-for="(item, index) in items"
        :key="index"
        :href="item.link"
        class="mx-4 my-4"
        target="_blank"
        variant="text"
      >
      <v-icon size="24px">{{ item.icon }}</v-icon>
    </v-btn>
    </div>

    <div class="pt-0">
      The app creators always aim to create excellent products that solve
      complex problems and help users save time and effort. With a focus on user
      experience, they strive to create products that make it easier and more
      convenient for users to do what they love.
    </div>

    <v-divider></v-divider>

    <div class="my-3">{{ new Date().getFullYear() }} — <strong>Nguyễn Thành Chung</strong></div>
  </v-footer>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          icon: 'mdi-youtube',
          link: 'https://www.youtube.com/channel/UCFZFsoJ4ziMeHGg_LC5YdgA',
        },
        { icon: 'mdi-facebook', link: 'facebook.com/chungdeptraivl' },
        {
          icon: 'mdi-instagram',
          link: 'https://www.instagram.com/chung_paylak22/',
        },
        { icon: 'mdi-github', lick: 'https://github.com/chungdeptraivl' },
      ],
    }
  },
}
</script>

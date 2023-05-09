<template>
  <div class="my-4" style="height: 645px;">
    <iframe width="100%" height="100%" allowfullscreen :src="getMovie" frameborder="0"></iframe>
  </div>
</template>

<script>
export default {
  props: {
    // eslint-disable-next-line vue/require-default-prop
    data: {
      type: Object,
    },
  },
  computed: {
    getMovie() {
        if(!this.data.videos) return
        const video = this.data.videos.results.find((e) => {
          return e.type === "Trailer"
        })
        return "https://www.youtube.com/embed/" + video.key
    },
  },
}
</script>

<style></style>

<template>
  <div
    class="display: flex; align-items: flex-start; justify-content: space-between; flex-direction: column;"
  >
    <span style="color: #fff"
      >Rating: ({{ data.vote_average }} / 10) of {{ data.vote_count }} votes</span
    >

    <v-rating
      :value="data.vote_average"
      half-increments
      length="10"
      color="#FFD700"
      size="20"
    ></v-rating>
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
}
</script>

<style></style>

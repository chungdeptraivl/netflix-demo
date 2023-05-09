<template>
    <div
      class="display: flex; align-items: flex-start; justify-content: space-between; flex-direction: column;"
    >
      <p style="color: #ba0c15; font-weight: bold;">Popularity:
        <span style="color: #fff"
      > ({{ data.popularity }} / 10) of votes</span
    >
    </p>
  
      <v-rating
        :value="data.popularity"
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
  
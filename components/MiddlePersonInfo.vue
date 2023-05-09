<template>
  <div
    style="
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      flex-direction: column;
    "
  >
    <h1 style="color: #fff; margin: 10px 0 10px 0">
      {{ data.name }}
    </h1>
    <p style="color: #ba0c15; font-weight: bold">
      Birthday:
      <span style="color: #fff">{{
        new Date(data.birthday).toLocaleString('en-us', {
          day: 'numeric',
          month: 'long',
          year: 'numeric',
        })
      }}</span>
    </p>
    <p style="color: #ba0c15; font-weight: bold">
      Deathday:
      <span style="color: #fff">{{
        new Date(data.deathday).toLocaleString('en-us', {
          day: 'numeric',
          month: 'long',
          year: 'numeric',
        })
      }}</span>
    </p>
    <p style="color: #ba0c15; font-weight: bold">
      Biography:
      <span style="color: #fff">{{ data.biography }}</span>
    </p>

    <rating-person :data="data" />
  </div>
</template>

<script>
import RatingPerson from './RatingPerson.vue'
export default {
  components: { RatingPerson },
  props: {
    // eslint-disable-next-line vue/require-default-prop
    data: {
      type: Object,
    },
  },
}
</script>

<style></style>

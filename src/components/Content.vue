<template>
  <main>
    <h2>Movies</h2>
    <div>
      <Card v-for="movie in movies" :key="movie.id" :details="movie" />
    </div>
  </main>
</template>

<script>
import Card from "@/components/Card";

export default {
  name: "Content",
  components: {
    Card,
  },
  props: {
    movies: Array,
  },
};
</script>

<style scoped></style>

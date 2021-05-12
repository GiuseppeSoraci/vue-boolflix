<template>
  <main>
    <!-- Movies -->
    <section v-show="movies.length" class="videos">
      <h2>Movies</h2>
      <div>
        <Card v-for="movie in movies" :key="movie.id" :details="movie" />
      </div>
    </section>

    <!-- Series -->
    <section v-show="series.length" class="videos">
      <h2>Tv Series</h2>
      <div>
        <Card v-for="serie in series" :key="serie.id" :details="serie" />
      </div>
    </section>
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
    series: Array,
  },
};
</script>

<style scoped></style>

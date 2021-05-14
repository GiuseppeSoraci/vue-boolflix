<template>
  <main>
    <div id="videos" v-if="movies.length !== 0 || series.length !== 0">
      <!-- Movies -->
      <section v-show="movies.length">
        <div>
          <h2>Movies</h2>
          <Card v-for="movie in movies" :key="movie.id" :details="movie" />
        </div>
      </section>

      <!-- Series -->
      <section v-show="series.length">
        <div>
          <h2>Series</h2>
          <Card v-for="serie in series" :key="serie.id" :details="serie" />
        </div>
      </section>
    </div>

    <div v-else>
      <section id="homepage">
        <h1>Film, serie TV e tanto altro. Senza limiti.</h1>
        <h2>Guarda ciò che vuoi ovunque. Disdici quando vuoi.</h2>
        <h3>
          Vuoi guardare GiusFlix? Cerca ciò che desideri in alto a destra.
        </h3>
      </section>
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
    series: Array,
  },
};
</script>

<style scoped>
main {
  min-height: 100vh;
  background-color: brown;
}
#homepage {
  text-align: center;
  padding-top: 150px;
  color: #fff;
}
#videos {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  position: relative;
}

h2 {
  text-align: center;
  color: #fff;
  padding: 30px 10px;
}
</style>

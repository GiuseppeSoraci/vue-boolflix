<template>
  <div id="app">
    <Header @search="getData" />
    <Content :movies="movieList" :series="tvList" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header";
import Content from "@/components/Content";

export default {
  name: "App",
  components: {
    Header,
    Content,
  },
  data() {
    return {
      apiURL: "https://api.themoviedb.org/3/search/",
      apiKey: "a0c03e15c33fc7a6d37d311319a6638c",
      movieList: [],
      tvList: [],
    };
  },
  methods: {
    getData(searchText) {
      console.log(searchText);

      if (searchText !== "") {
        const apiParams = {
          api_key: this.apiKey,
          query: searchText,
          language: "it-IT",
        };

        // Movies
        axios
          .get(this.apiURL + "movie", {
            params: apiParams,
          })
          .then((res) => {
            this.movieList = res.data.results;
          });

        // Series
        axios
          .get(this.apiURL + "tv", {
            params: apiParams,
          })
          .then((res) => {
            this.tvList = res.data.results;
          });
      }
    },
  },
};
</script>

<style lang="scss"></style>

<template>
  <div>
    <img
      v-if="details.poster_path"
      :src="`https://image-tmdb.org/t/p/w342${details.poster_path}`"
    />
    <img
      v-else
      src="https://www.altavod.com/assets/images/poster-placeholder.png"
    />

    <ul>
      <li>{{ details.title ? details.title : details.name }}</li>
      <li>
        {{
          details.original_title
            ? details.original_title
            : details.original_name
        }}
      </li>
      <li>
        <img
          v-if="isFlag(details.original_language)"
          :src="require(`@/assets/img/flags/${details.original_language}.png`)"
          :alt="details.original_language"
        />
        <span v-else>{{ details.original_language }}</span>
      </li>
      <li>
        <i
          v-for="i in getStarVote(etails.vote_average)"
          :key="`full-${i}`"
          class="fas fa-star"
        ></i>
        <i
          v-for="i in 5 - getStarVote(details.vote_average)"
          :key="`empty-${i}`"
          class="far fa-star"
        ></i>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    details: Object,
  },
  data() {
    return {
      flagsImg: ["it", "en"],
    };
  },
  methods: {
    isFlag(lang) {
      return this.flagsImg.includes(lang);
    },
    getStarVote(vote) {
      return Math.cell(vote / 2);
    },
  },
};
</script>

<style scoped>
li img {
  width: 32px;
}
</style>

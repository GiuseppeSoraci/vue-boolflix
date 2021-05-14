<template>
  <section class="card">
    <!-- Poster -->
    <img
      class="poster"
      v-if="details.poster_path"
      :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`"
    />
    <img
      class="notimg"
      v-else
      src="https://www.altavod.com/assets/images/poster-placeholder.png"
    />

    <!-- Title -->
    <ul>
      <li>
        <h4>
          {{ details.title ? details.title : details.name }}
        </h4>
      </li>
      <li>
        <h4>
          {{
            details.original_title
              ? details.original_title
              : details.original_name
          }}
        </h4>
      </li>

      <!-- Language -->
      <li>
        <img
          class="flag"
          v-if="isFlag(details.original_language)"
          :src="require(`@/assets/img/flags/${details.original_language}.png`)"
          :alt="details.original_language"
        />
        <span v-else>{{ details.original_language }}</span>
      </li>

      <!-- Vote -->
      <li>
        <i
          v-for="i in getStarVote(details.vote_average)"
          :key="`full-${i}`"
          class="fas fa-star"
        ></i>
        <i
          v-for="i in 5 - getStarVote(details.vote_average)"
          :key="`empty-${i}`"
          class="far fa-star"
        ></i>
      </li>

      <!-- Overview -->
      <li class="layover">
        <p class="overview">{{ details.overview }}</p>
      </li>
    </ul>
  </section>
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
      return Math.ceil(vote / 2);
    },
  },
};
</script>

<style scoped lang="scss">
.card {
  flex-basis: 250px;
  margin: 10px;
  text-align: center;
  position: relative;
}

.card:hover .layover {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  position: absolute;
  top: 0;
  left: 0;
}
.card .poster {
  border-radius: 5%;
}

.card .poster {
  height: 484px;
}

.overview {
  display: none;
}

.card:hover .layover .overview {
  display: block;
  position: absolute;
  top: 15%;
  left: 50%;
  transform: translate(-50%);
  font-size: 15px;
  margin-bottom: 15px;
  color: #fff;
}

h4 {
  font-size: 20px;
}

.notimg {
  width: 342px;
  height: 484px;
  border-radius: 5%;
}

.card .flag {
  width: 30px;
}

i {
  color: rgb(216, 202, 7);
}
</style>

<template>
  <div>
    <ul>
      <li>{{ details.title }}</li>
      <li>{{ details.original_title }}</li>
      <li>
        <img v-if="isFlag(details.original_language)" src="" alt="" />
        <span v-else>{{ details.original_language }}</span>
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
  },
};
</script>

<style></style>

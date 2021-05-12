<template>
  <header>
    <img src="../assets/img/logo.png" alt="logo" />

    <div>
      <input type="text" placeholder="Search" v-model.trim="searchText" />
      <button @click="$emit('search', searchText)">Search</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
}
</style>

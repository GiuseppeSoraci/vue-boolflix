<template>
  <header>
    <!-- Logo -->
    <img class="logo" src="../assets/img/logo.png" alt="logo" />

    <!-- Searchbar -->
    <div class="search">
      <input type="text" placeholder="Search" v-model.trim="searchText" />
      <button @click="$emit('search', searchText)">
        <i class="fa fa-search" />
      </button>
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
  align-items: center;
  height: 80px;
  background-color: black;
}

.logo {
  height: 60px;
  margin-left: 25px;
}

input {
  width: 300px;
  border-radius: 20px;
  padding: 10px;
  margin-right: 10px;
}

button {
  background: transparent;
  border: none;
  margin-right: 30px;
}

i {
  font-size: 20px;
  border: none;
  color: brown;
}

i:hover {
  color: red;
}
</style>

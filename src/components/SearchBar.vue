<template>
  <div>
    <h1>Search Bar</h1>
    <input
      type="text"
      name="search-bar"
      value=""
      placeplaceholder="Search Here..."
      v-model="searchQuery"
    />
    <button type="button" name="button" v-on:click="onInput">Search</button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data: () => {
    return {
      searchQuery: ""
    };
  },
  methods: {
    onInput: function() {
      this.$emit("termChange", this.searchQuery);
    }
  }
};
</script>

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>

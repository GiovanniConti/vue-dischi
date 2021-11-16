<template>
  <select class="form-select" aria-label="Default select example" 
    v-model="selectedGenre"
    @change="filterSelected"
    >
    <option disabled>Select a genre</option>
    <option selected>All</option>
    <option
      v-for="(genre, i) in availableGenres"
      :key="i"
      :value="genre">{{ genre }}</option>
  </select>
</template>

<script>
export default {
  name: "FiltersSection",
  props: {
    availableGenres: Array
  },
  data() {
    return {
      selectedGenre: "",
    }
  },
  methods: {
    filterSelected() {
      this.$emit("filterSelected", this.selectedGenre)
    }
  }
}
</script>

<style>

</style>
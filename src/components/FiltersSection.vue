<template>
  <select class="form-select" aria-label="Default select example" v-model="selectedGenre">
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
}
</script>

<style>

</style>
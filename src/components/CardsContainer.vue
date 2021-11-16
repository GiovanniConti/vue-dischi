<template>
  <div class="cardsCotainer container-lg my-5">
    <div class="row justify-content-center pb-5">
      <div class="col-6">
        <FiltersSection
          :availableGenres="genreList"
          @filterSelected= "onGenreFilter"
        ></FiltersSection>
      </div>
    </div>
    <div class="row row-cols-5 g-4">
      <div class="col d-flex"
        v-for="(disc, i) in filteredDiscList"
        :key="i"
      >
        <DiscCard
        :image="disc.poster"
        :title="disc.title"
        :author="disc.author"
        :year="disc.year"
        ></DiscCard>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import DiscCard from './DiscCard.vue';
import FiltersSection from './FiltersSection.vue';

export default {
  name: "CardsContianer",
  components: {
    DiscCard,
    FiltersSection,
  },
  data() {
    return {
      discList: [],
      filteredDiscList: [],
    };
  },
  computed: {
    genreList() {
      const genreList = [];

      this.discList.forEach((disc) => {
        if(!genreList.includes(disc.genre)){
          genreList.push(disc.genre);
        }
      });
      return genreList;
    },
  },
  methods: {
    fetchData(url) {
      axios.get(url).then((apiResp) => {
        this.discList = apiResp.data.response;
      });
    },
    onGenreFilter(filter){
      console.log("Filter called", filter);
      if(filter === "All"){
        console.log("log inside filter if");
        this.filteredDiscList = this.discList
      } else {
          this.filteredDiscList = this.discList.filter(el => {
            return el.genre === filter;
          });
        }

        console.log("log di filtered list", this.filteredDiscList);
    }
  },
  mounted() {
    this.fetchData("https://flynn.boolean.careers/exercises/api/array/music");
    setTimeout(() => {
      this.onGenreFilter("All")
    }, 500);
  }

}
</script>

<style lang="scss">

</style>
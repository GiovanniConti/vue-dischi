<template>
  <div class="cardsCotainer container-lg my-5">
    <div class="row justify-content-center pb-5">
      <div class="col-6">
        <FiltersSection
          :availableGenres="genreList"
          @filterSelected= "selectedFilter"
        ></FiltersSection>
      </div>
    </div>
    <div class="row row-cols-5 g-4">
      <div class="col d-flex"
        v-for="(disc, i) in filteredList"
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
      selectedGenre: "All",
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
    filteredList(){
      let filteredDiscList = this.discList
      if(this.selectedGenre != "All"){
        filteredDiscList = this.discList.filter(el => {
          return el.genre === this.selectedGenre;
        });
      }
        return filteredDiscList;
    }
  },
  methods: {
    fetchData(url) {
      axios.get(url).then((apiResp) => {
        this.discList = apiResp.data.response;
      });
    },
    selectedFilter(filter){
      this.selectedGenre = filter;
    }
  },
  mounted() {
    this.fetchData("https://flynn.boolean.careers/exercises/api/array/music");
  }

}
</script>

<style lang="scss">

</style>



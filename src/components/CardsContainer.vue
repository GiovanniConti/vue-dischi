<template>
  <div class="cardsCotainer container-lg my-5">
    <div class="row row-cols-5 g-4">
      <div class="col d-flex"
        v-for="(disc, i) in discList"
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
import DiscCard from './DiscCard.vue';
import axios from 'axios';

export default {
  name: "CardsContianer",
  components: {
    DiscCard,
  },
  data() {
    return {
      discList: [],
    };
  },
  methods: {
    fetchData(url) {
      axios.get(url).then((apiResp) => {
        this.discList = apiResp.data.response;
      });
    }
  },
  mounted() {
    this.fetchData("https://flynn.boolean.careers/exercises/api/array/music");
  }

}
</script>

<style lang="scss">

</style>
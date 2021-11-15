<template>
  <main>
    <CardsContainer></CardsContainer>
  </main>
</template>

<script>
import CardsContainer from './CardsContainer.vue'


export default {
  name: "Main",
  components: {
    CardsContainer,
  },

}
</script>

<style lang="scss">
  
  main{
    margin: auto;
  }
</style>
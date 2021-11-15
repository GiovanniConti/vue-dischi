<template>
  <div class="card p-4">
    <img class="card-img-top" :src="image" :alt="title">
    <div class="card-body text-center p-0">
      <h5 class="card-title fs-3 pt-5 pb-3">{{ title.toUpperCase() }}</h5>
      <h6 class="card-text fs-4 mb-0">{{ author }}</h6>
      <h6 class="card-text fs-5">{{ year }}</h6>
    </div>
  </div>
</template>

<script>
export default {
  name: "DiscCard",
  props: ["image", "title", "author", "year"],

}
</script>

<style lang="scss">
  .card{
    background-color: #374753!important;

    .card-body{

      h5{
        color: white;
        font-weight: 900;
      }
      h6{
        color: gray;
      }
    }
  }

</style>
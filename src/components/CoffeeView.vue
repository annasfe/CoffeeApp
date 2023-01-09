<template>
  <div>
    <h2>Pick a favorite:</h2>
    <label for="filter">Filter</label>
    <input type="text" v-model="searchTerm" @keyup="filter" />
    <div id="container-grid">
      <coffee-grid :coffees="filteredCoffees" @setFeatureEvent="setFeature" />
      <featured
        :featuredCoffee="featuredCoffee"
        :class="{ hide: !featuredCoffee.img }"
      />
    </div>
  </div>
</template>

<script>
import CoffeeGrid from "./CoffeeGrid.vue";
import Featured from "./Featured.vue";

export default {
  name: "CoffeeView",
  components: {
    CoffeeGrid,
    Featured,
  },
  data() {
    return {
      featuredCoffee: {
        name: "",
        img: "",
      },
      searchTerm: "",
      filteredCoffees: this.allCoffees,
    };
  },
  //data that are passed by parent
  props: {
    allCoffees: Array,
  },
  methods: {
    setFeature(coffee) {
      this.featuredCoffee = coffee;
    },
    filter() {
      this.filteredCoffees = this.allCoffees.filter((item) =>
        item.name.includes(this.searchTerm)
      );
    },
  },
  // computed: {
  //   filteredCoffees() {
  //     return this.allCoffees.filter((item) =>
  //       item.name.includes(this.searchTerm)
  //     );
  //   },
  // },
};
</script>

<style scoped>
#container-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  margin-top: 50px;
}

.hide {
  display: none;
}
</style>

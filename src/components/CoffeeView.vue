<template>
  <div>
    <h2>Place your order:</h2>
    <div id="container-grid">
      <Grid :coffees="allCoffees" @setFeatureEvent="setFeature" />
      <Cart :chosenItems="chosenItems" :class="{ hide: !chosenItems.length }" />
    </div>
  </div>
</template>

<script>
import Grid from "./Grid.vue";
import Cart from "./Cart.vue";

export default {
  name: "CoffeeView",
  components: {
    Grid,
    Cart,
  },
  data() {
    return {
      searchTerm: "",
      chosenItems: [],
    };
  },
  //data that are passed by parent
  props: {
    allCoffees: Array,
  },
  methods: {
    setFeature(coffee) {
      this.chosenItems.push(coffee);
    },
  },
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

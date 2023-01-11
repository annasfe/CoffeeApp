<template>
  <div>
    <h2>Place your order:</h2>
    <div id="container-grid">
      <coffee-grid :coffees="allCoffees" @setFeatureEvent="setFeature" />
      <featured :cart="cart" :class="{ hide: !cart.length }" />
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
      searchTerm: "",
      cart: [],
    };
  },
  //data that are passed by parent
  props: {
    allCoffees: Array,
  },
  methods: {
    setFeature(coffee) {
      this.cart.push(coffee);
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

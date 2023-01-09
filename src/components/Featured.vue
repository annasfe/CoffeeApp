<template>
  <div id="featured">
    <h2>Your order:</h2>
    <div v-for="coffee in cart" :key="coffee.id">
      <h3>
        {{ coffee.name }}
        <span style="color: green"> - {{ coffee.price }}</span>
      </h3>
    </div>
    <hr />

    <h3 style="color: red">Total : {{ total }}</h3>
  </div>
</template>

<script>
export default {
  name: "Featured",
  props: ["cart"],
  computed: {
    total() {
      return this.cart.reduce((acc, item) => acc + item.price, 0);
    },
  },
};
</script>

<style></style>

<template>
  <div id="featured">
    <h2>Your order:</h2>
    <div v-for="coffee in cart" :key="coffee.id">
      <h4>
        {{ coffee.name }}
        <span style="color: green"> - {{ coffee.price }}</span>
      </h4>
    </div>
    <hr />

    <h4 style="color: red">Total : {{ total }}</h4>
  </div>
</template>

<script>
export default {
  name: "Featured",
  props: ["cart"],

  //we could have as computed here or
  //we could calculate on clicking some button or
  //we could compute on higher level and send just the total as prop
  computed: {
    total() {
      return this.cart.reduce((acc, item) => acc + item.price, 0).toFixed(2);
    },
  },
};
</script>

<style>
#featured {
  text-align: left;
}
</style>

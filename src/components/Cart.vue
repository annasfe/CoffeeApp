<template>
  <div id="featured">
    <h2>Your order:</h2>
    <div v-for="coffee in chosenItems" :key="coffee.id">
      <h5>
        {{ coffee.name }}
        <span style="color: green"> - {{ coffee.price }}</span>
      </h5>
    </div>
    <hr />

    <h5 style="color: red">Total : {{ total }}</h5>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: ["chosenItems"],

  //we could have as computed here or
  //we could calculate on clicking some button or
  //we could compute on higher level and send just the total as prop
  computed: {
    total() {
      return this.chosenItems
        .reduce((acc, item) => acc + item.price, 0)
        .toFixed(2);
    },
  },
};
</script>

<style>
#featured {
  text-align: left;
}
</style>

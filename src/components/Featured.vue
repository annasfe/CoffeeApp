<template>
  <div id="featured">
    <div>
      <img :src="featuredCoffee.img" />
      <h3>{{ featuredCoffee.name }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "Featured",
  props: ["featuredCoffee"],
};
</script>

<style></style>

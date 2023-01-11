<template>
  <div id="grid">
    <div v-for="coffee in coffees" :key="coffee.id">
      <img :src="coffee.img" @click="handleClick(coffee)" />
      <h5>{{ coffee.name }} ({{ coffee.price }}€)</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: "Grid",
  props: ["coffees"],
  methods: {
    handleClick(coffee) {
      this.$emit("setFeatureEvent", coffee);
    },
  },
};
</script>

<style>
#grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-auto-rows: 180px;
  gap: 50px;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  cursor: pointer;
}
</style>

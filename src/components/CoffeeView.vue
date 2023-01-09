<template>
  <div>
    <h2>Pick a favorite:</h2>
    <div id="container-grid">
      <div id="grid">
        <div v-for="coffee in allCoffees" :key="coffee.name">
          <img :src="coffee.img" @click="handleClick(coffee)" />
          <h5>{{ coffee.name }} ({{ coffee.price }}€)</h5>
        </div>
      </div>
      <div id="featured" :class="{ hide: !featuredCoffee.img }">
        <div>
          <img :src="featuredCoffee.img" />
          <h3>{{ featuredCoffee.name }}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CoffeeView",
  data() {
    return {
      featuredCoffee: {
        name: "",
        img: "",
      },
    };
  },
  //data that are passed by parent
  props: {
    allCoffees: Array,
  },
  methods: {
    handleClick(coffee) {
      this.featuredCoffee.name = coffee.name;
      this.featuredCoffee.img = coffee.img;
    },
  },
};
</script>

<style scoped>
#container-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}

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

.hide {
  display: none;
}
</style>

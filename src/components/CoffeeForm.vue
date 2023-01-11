<template>
  <div>
    <h2>Add a coffee</h2>
    <form @submit.prevent="addCoffee">
      <input type="text" v-model="coffeeName" placeholder="name" />
      <input type="text" v-model="coffeePrice" placeholder="price" />
      <input id="imgC" type="url" v-model="coffeeImg" placeholder="image URL" />

      <button type="submit">Add Coffee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "CoffeeForm",
  data() {
    return {
      coffeeName: "",
      coffeeImg: "",
      coffeePrice: 0,
      id: 7,
    };
  },
  //data that are passed by parent
  methods: {
    addCoffee() {
      this.id++;
      let newCoffee = {
        id: this.id,
        name: this.coffeeName,
        img: this.coffeeImg,
        price: this.coffeePrice,
      };
      this.$emit("add", newCoffee);
      this.coffeeName = this.coffeeImg = "";
      this.coffeePrice = 0;
    },
  },
};
</script>

<style scoped>
input {
  margin: 10px;
}

form {
  padding: 0 100px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}

#imgC,
button {
  grid-column: 1 / span 2;
}

button {
  margin: 0 180px;
}
</style>

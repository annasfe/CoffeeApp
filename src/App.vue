<template>
  <main>
    <nav>
      <button @click="cafeView = false" class="btn btn-warning">
        Add coffee
      </button>
      <button @click="cafeView = true" class="btn btn-warning">
        Choose your cup
      </button>
    </nav>
    <div class="container">
      <h1>My coffee app <span style="font-size: 100px">&#9749;</span></h1>
      <CoffeeForm v-if="!cafeView" @add="addCoffee" />
      <CoffeeView v-else :allCoffees="allCoffees" />
    </div>
  </main>
</template>

<script>
//Tell JS where to find the components
import CoffeeForm from "./components/CoffeeForm.vue";
import CoffeeView from "./components/CoffeeView.vue";
import MyData from "./MyData";

export default {
  name: "App",

  //tell vue which components we use
  components: {
    CoffeeView,
    CoffeeForm,
  },

  //reactive data that when changed will update the View
  data() {
    return {
      cafeView: true,
      allCoffees: [],
    };
  },
  methods: {
    addCoffee(coffee) {
      this.allCoffees.push(coffee);
      this.cafeView = true;
    },
  },
  //lifecycle hook, load the external data only once, when component is created
  created() {
    this.allCoffees = MyData;
  },
};
</script>

<style>
nav {
  text-align: right;
}
.container {
  max-width: 800px;
  margin: 20px auto;
  text-align: center;
}
h1 {
  color: green;
  font-size: 40px;
  padding-bottom: 30px;
}

button {
  margin: 10px;
}
</style>

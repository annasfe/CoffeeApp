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
      <CoffeeForm :class="{ hide: cafeView }" @add="addCoffee" />
      <CoffeeView :class="{ hide: !cafeView }" :allCoffees="allCoffees" />
    </div>
  </main>
</template>

<script>
//Tell JS where to find the components
import CoffeeForm from "./components/CoffeeForm.vue";
import CoffeeView from "./components/CoffeeView.vue";
import CoffeeData from "./MyData";
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
      cafeView: false,
      allCoffees: CoffeeData,
    };
  },
  methods: {
    addCoffee(coffee) {
      this.allCoffees.push(coffee);
      console.log(this.allCoffees);
      this.cafeView = true;
    },
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
.hide {
  display: none;
}
</style>

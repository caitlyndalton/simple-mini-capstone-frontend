<script>
var axios = require("axios");

export default {
  data: function () {
    return {
      products: [],
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("http://localhost:3000/products.json").then((response) => {
        console.log("All products", response.data);
        this.products = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>All Products</h1>
    <div v-for="product in products" v-bind:key="product.id">
      <h2>Name: {{ product.name }}</h2>
      <p>Price: {{ product.price }}</p>
      <p>Image: {{ product.image_url }}</p>
      <img v-bind:src="product.image_url" v-bind:alt="product.name" />
    </div>
  </div>
</template>

<style>
.home img {
  width: 100px;
}
</style>

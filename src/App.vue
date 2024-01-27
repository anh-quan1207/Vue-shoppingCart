<template>
  <header>
    <TheHeader :cardList="carList"></TheHeader>
  </header>
  <main class="mt-5 container">
    <ProductList @handle-buy="handleBuy"></ProductList>
  </main>
</template>

<script>
import TheHeader from "./components/TheHeader.vue"
import ProductList from "./components/ProductList.vue"
export default {
  name: 'App',
  components: {
    TheHeader, ProductList
  },
  data() {
    return {
      carList: [],
    }
  },
  methods: {
    handleBuy(productItem) {
      // const index = this.carList.findIndex(cart => cart.id === productItem.id)
      this.carList.push(productItem);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

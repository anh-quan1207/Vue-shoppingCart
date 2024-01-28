<template>
  <header>
    <TheHeader :cardList="carList" @handleDelete="handleDelete"></TheHeader>
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
      const index = this.carList.findIndex(cart => cart.id === productItem.id);
      if (index !== -1) {
        this.carList[index].amount += 1;
      } else {
        const newProductItem = {...productItem, amount: 1};
        this.carList = [...this.carList, newProductItem];
      }
    },
    handleDelete(card) {
      this.carList = this.carList.filter(cardItem => cardItem.id !== card.id);
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

<script>
  export default {
    props: {
      productItem: {
        type: Object
      }
    },
    methods: {
      handleBuy(productItem) {
        this.$emit('handle-buy', productItem);
      }
    }
  }
</script>

<template>
  <div class="card text-left mb-3">
    <img class="card-img-top mt-2" :src="productItem.image" alt="">
    <div class="card-body">
      <h4 class="card-title font-weight-bold">{{ productItem.name }}</h4>
      <p class="card-text text-danger">{{ productItem.price }}</p>
    </div>
    <div class="mb-2">
      <button class="btn btn-danger ml-2" @click="handleBuy(productItem)">Buy</button>
      <button class="btn btn-info ml-2">Detail</button>
    </div>
  </div>
</template>

<style scoped>

</style>
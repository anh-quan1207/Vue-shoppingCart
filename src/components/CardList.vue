<script>
  export default {
    props: {
      cardList: {
        type: Array,
      }
    },
    computed: {
      sumMoney() {
        return this.cardList.reduce((sum, card) => sum += card.amount * card.price, 0);
      }
    },
    methods: {
      handleDelete(card) {
        this.$emit("handleDelete", card);
      }
    }
  }
</script>

<template>
  <table class="table">
    <thead>
    <tr>
      <th>N.o</th>
      <th>Name</th>
      <th>Price</th>
      <th>Remain</th>
      <th>Amount</th>
      <th>Total</th>
      <th>Action</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="(card, index) in cardList" :key="index">
      <td scope="row">{{ index+1 }}</td>
      <td>{{ card.name }}</td>
      <td>{{ card.price }}</td>
      <td>{{ card.quantityInStock }}</td>
      <td>
<!--        <button class="btn btn-success">-->
<!--          <i class="fa fa-arrow-up"></i>-->
<!--        </button>-->
        <span class="mx-2">{{ card.amount }}</span>
<!--        <button class="btn btn-success">-->
<!--          <i class="fa fa-arrow-down"></i>-->
<!--        </button>-->
      </td>
      <td>{{ card.amount * card.price }}</td>
      <td>
        <button class="btn btn-danger" @click="handleDelete(card)">
          <i class="fa fa-trash"></i>
        </button>
      </td>
    </tr>
    <tr>
      <td scope="row">Total</td>
      <td scope="row"></td>
      <td scope="row"></td>
      <td scope="row"></td>
      <td scope="row"></td>
      <td scope="row">{{ sumMoney }}</td>
      <td scope="row"></td>
    </tr>
    </tbody>
  </table>
</template>

<style scoped>

</style>
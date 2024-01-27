<script>
import CardList from "./CardList.vue"
  export default {
    props: {
      cardList: {
        type: Array,
      }
    },
    components: {CardList},
    data() {
      return {
        isOpenModalCartList: false,
      }
    },
    methods: {
      handleOpenModalCardList() {
        this.isOpenModalCartList = true
      },
      handleCloseModalCardList() {
        this.isOpenModalCartList = false
      }
    },
  }
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <a class="navbar-brand logo" href="#">CardVue</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            Dropdown
          </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">Action</a>
            <a class="dropdown-item" href="#">Another action</a>
            <div class="dropdown-divider"></div>
            <a class="dropdown-item" href="#">Something else here</a>
          </div>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" href="#">Disabled</a>
        </li>
      </ul>
      <form class="form-inline my-2 my-lg-0">
        <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
      </form>
      <div>
        <button class="btn btn-danger ml-2" @click="handleOpenModalCardList">
          <i class="fa fa-shopping-cart"></i>
          <span class="badge badge-light ml-2">0</span>
        </button>
      </div>
    </div>
  </nav>
  <teleport to="#app">
    <AppModal :isOpen="isOpenModalCartList" :handleCloseModal="handleCloseModalCardList" >
      <section>
        <CardList :cardList="cardList"></CardList>
      </section>
    </AppModal>
  </teleport>
</template>

<style scoped>
  .logo {
    color: green;
  }
</style>
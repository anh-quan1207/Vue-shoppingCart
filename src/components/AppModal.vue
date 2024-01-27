<script>
  export default {
    props: {
      isOpen: {
        type: Boolean,
      },
      handleCloseModal: {
        type: Function,
      }
    },
    methods: {
      handleClose() {
        this.handleCloseModal();
      }
    }
  }
</script>

<template>
  <div v-if="isOpen" class="modal" @click="handleClose">
    <div class="modal-container" @click.stop>
      <div class="modal-header">
        <h1 class="modal-title">Cart</h1>
        <div class="modal-close" @click="handleClose">
          <i class="fa fa-times"></i>
        </div>
      </div>
      <div class="modal-body">
        <slot></slot>
      </div>
      <div class="modal-footer"></div>
    </div>
  </div>
</template>

<style scoped>
.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  display: flex;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4); /* Black w/ opacity */
}
.modal-container {
  width: 950px;
  margin: auto;
  margin-top: 70px;
  background-color: white;
  border: 1px solid #888;
  padding: 10px 20px;
}
.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.modal-header .modal-close {
  width: 50px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  border-radius: 50%;
  font-size: 30px;
}
.modal-header .modal-close:hover {
  background-color: rgba(0, 0, 0, 0.2);
  cursor: pointer;
}
</style>
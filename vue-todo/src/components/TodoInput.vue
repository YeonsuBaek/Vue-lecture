<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo" />
    <span class="addContainer" @click="addTodo">
      <i class="fa fa-plus addBtn"></i>
    </span>

    <ModalComponent :show="showModal" @close="showModal = false">
      <h3 slot="header">
        경고!
        <i class="closeModalBtn fa fa-times" @click="showModal = false"></i>
      </h3>

      <p slot="body">아무것도 입력하지 않았습니다</p>
    </ModalComponent>
  </div>
</template>

<script>
import ModalComponent from "./common/ModalComponent";

export default {
  components: {
    ModalComponent,
  },
  data() {
    return {
      newTodoItem: "",
      showModal: false,
    };
  },
  methods: {
    addTodo: function () {
      if (this.newTodoItem !== "") {
        this.$emit("addTodoItem", this.newTodoItem);
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput: function () {
      this.newTodoItem = "";
    },
  },
};
</script>

<style scoped>
input:focus {
  outline: none;
}

.inputBox {
  position: relative;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  background: #fff;
}

.inputBox input {
  margin-left: 1.5rem;
  margin-right: 4.5rem;
  width: calc(100% - 6rem);
  font-size: 0.9rem;
  border-style: none;
}

.addContainer {
  position: absolute;
  top: 0;
  right: 0;
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
  background: linear-gradient(to right, #6478fb, #8763fb);
  cursor: pointer;
}

.addBtn {
  color: #fff;
  vertical-align: middle;
}

.closeModalBtn {
  color: #42b983;
}
</style>

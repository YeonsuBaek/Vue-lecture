<template>
  <div>
    <ul>
      <li v-for="todoItem in todoItems" :key="todoItem">{{ todoItem }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todoItems: [],
    };
  },
  created() {
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
        // console.log(localStorage.key(i));
      }
    }
  },
};
</script>

<style scoped></style>

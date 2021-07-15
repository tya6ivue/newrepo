<template>
  <div>
    <h1>
      Type here and press add to add the data or press the X to delete the data
    </h1>
    <form v-on:submit.prevent="addTodo" name="myForm">
      <input type="text" v-model="currentTodos" />
      <button type="submit">Add</button>
    </form>
    <ul class="formm">
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo.id }} {{ todo.value }}
        <button v-on:click="deleteItem(index)">X</button>
        <button v-on:click="editItem(todo)">Edit</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data: function () {
    return {
      id: [],
      value: [],
      todos: [
        { id: 1, value: "first" },
        { id: 2, value: "second" },
        { id: 3, value: "third" },
        { id: 4, value: "fourth" },
        { id: 5, value: "fifth" },
      ],
      currentTodos: "",
      editData: {},
    };
  },
  methods: {
    addTodo: function () {
      if (this.editData.id) {
        const index = this.todos.findIndex((el) => el.id === this.editData.id);

        this.todos[index].value = this.currentTodos;
      } else {
        this.todos.push({
          id: Math.floor(Math.random() * 100),
          value: this.currentTodos,
        });
      }
      this.currentTodos = "";
      this.editData = {};
    },
    deleteItem: function (index) {
      this.todos.splice(index, 1);
    },
    editItem: function (param) {
      this.currentTodos = param.value;
      this.editData = param;
    },
  },
};
</script>
<style scoped>
.formm {
  overflow: hidden;
}
</style>
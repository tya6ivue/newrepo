<template>
  <div>
    <h1>
      Type here and press add to Add the data or press the X to delete the data
    </h1>
    <form class="form" v-on:submit.prevent="addItem" name="myForm">
      <input type="text" v-model="currentTodos" />
      <button type="submit">Add</button>
    </form>

    <ul class="ull">
      <li class="tr"></li>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo.id }}
        <input
          type="text"
          v-model="todo.value"
          v-if="editData.id === todo.id"
        />
        {{ editData.id === todo.id ? "" : todo.value }}
        <button class="btn" v-on:click="deleteItem(index)">X</button>

        <button>
          <span @click="editItem(todo)" v-if="editData.id !== todo.id"
            >edit</span
          ><span @click="editItem" v-if="editData.id === todo.id">Update</span>
        </button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data: function () {
    return {
      todos: [
        { id: 1, value: "first" },
        { id: 2, value: "second" },
        { id: 3, value: "third" },
        { id: 4, value: "fourth" },
        { id: 5, value: "fifth" },
      ],
      currentTodos: "",
      editData: {},
      boolean: false,
      add: "",
      newModel: [],
    };
  },
  methods: {
    abc: function () {
      this.boolean = false;
    },
    abd: function () {
      this.boolean = true;
    },

    addItem: function () {
      this.todos.push({
        id: Math.floor(Math.random() * 100),
        value: this.currentTodos,
      });
      this.currentTodos = "";
    },
    deleteItem: function (index) {
      this.todos.splice(index, 1);
    },

    editItem: function (param) {
      this.editData = param;
    },
  },
};
</script>
<style scoped>
.ull {
  width: 50%;
}

.form {
  width: 50%;
}
.li {
  list-style-type: none;
  padding: 10px;
  color: aqua;
  border: 1px dodgerblue;
}
.ull li {
  list-style-type: none;
  border: 1px solid black;
  margin-right: 10px;
}
.btn {
  margin-right: 5px;
  margin-left: 10px;
}
</style>
<template>
  <div class="home">
    <Header />
    <AddTodo @add-todo="addTodo" />
    <Todos :todos="todos" @del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from "../components/layout/Header";
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import * as axios from "axios";

export default {
  name: "Home",
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => (this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err)));
    },
    addTodo(newTodo) {
      const {title, completed } = newTodo;

      axios
        .post(`https://jsonplaceholder.typicode.com/todos `, {
          title,
          completed
        })
        .then(res => (this.todos = [...this.todos, {...res.data, id: this.todos[this.todos.length - 1].id+1}]))
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/todos?_limit=5`)
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  }
};
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background-color: #666;
}
</style>
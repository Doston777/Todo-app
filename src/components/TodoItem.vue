<template>
  <div class="todo-item" :class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-model="todo.completed">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f5f5f5;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: red;
  color: white;
  border: none;
  padding: 2px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
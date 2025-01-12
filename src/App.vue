<template>
  <div id="app">
    <h1>Vue To-Do List</h1>
    <input v-model="newTodoText" @keyup.enter="addTodo" placeholder="Add a new task" />
    <ul>
      <TodoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        @remove="removeTodo(index)"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';

export default {
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodoText: '',
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoText.trim()) {
        this.todos.push({ text: this.newTodoText, completed: false });
        this.newTodoText = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  border-bottom: 1px solid #ddd;
}
input[type='text'] {
  width: 80%;
  padding: 8px;
}
button {
  background-color: #f44336;
  color: white;
  border: none;
  padding: 8px 16px;
  cursor: pointer;
}
button:hover {
  background-color: #d32f2f;
}
</style>

<template>
  <div id="app">
    <h1>What's Todo?</h1>
    <input type="text" placeholder="What would you like todo?" v-on:keyup.enter="addTodo" />
    <ul>
      <TodoItem v-for="todo in todos" v-bind:todo="todo" v-bind:key="todo.id" v-on:remove-todo="removeTodo"></TodoItem>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'app',
  data: function() {
    return {
      todos: [
        { name: 'Todo 1', isComplete: false, id: Date.now() },
        { name: 'Todo 2', isComplete: false, id: Date.now() + 1 }
      ]
    }
  },
  methods: {
    addTodo(e) {
      let todo = e.target.value;

      this.todos.push({ name: todo, isComplete: false, id: Date.now() });
      e.target.value = '';
    },
    removeTodo(id) {
      this.todos = this.todos.filter( todo => todo.id !== id );
    }
  },
  components: {
    TodoItem
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

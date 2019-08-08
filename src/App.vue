<template>
  <div id="app">
  <h1>Todo application</h1>
  <AddTodo @add-todo="addTodo" />
  <hr>
  <TodoList 
    v-bind:namevar="todos"
    @remove-todo="removeTodo"
  />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';
export default {
  name: 'app',
  data() {
    return {
      todos: [
        {id:1, title: 'Купить еды', completed: false},
        {id:2, title: 'Покормить кота', completed: false},
        {id:3, title: 'Закончить планировщик', completed: false},
      ]
    }
  },
  methods: {
    removeTodo(id) {
      console.log(id+" app")
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(toll) {
      this.todos.push(toll)
    }
  },
  components: {
    TodoList, AddTodo
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

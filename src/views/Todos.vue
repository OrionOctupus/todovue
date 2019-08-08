<template>
  <div>
  <h2>Todo application</h2>
  <router-link to="/">Home</router-link>
  <hr>
  <AddTodo @add-todo="addTodo" />
  <select v-model="filter">
      <option value="all">all</option>
      <option value="completed">competed</option>
      <option value="not-completed">not-completed</option>
  </select>
  <hr>
  <Loader v-if="loading"/>
  <TodoList
    v-else-if="filteredTodos.length"
    v-bind:namevar="filteredTodos"
    @remove-todo="removeTodo"
  />
  <p v-else>Todo list empty!</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';
import Loader from '@/components/Loader';
import { setTimeout } from 'timers';

export default {
  name: 'app',
  data() {
    return {
      todos: [
        // {id:1, title: 'Купить еды', completed: false},
        // {id:2, title: 'Покормить кота', completed: false},
        // {id:3, title: 'Закончить планировщик', completed: false},
      ],
      loading: true,
      filter: "all"
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
    .then(response => response.json())
    .then(json => {
        setTimeout(()=>{
            this.todos = json
            this.loading = false
        }, 1500)
     
    })
  },
//   watch: {
//       filter(value) {
//           console.log(value)
//       }
//   },
    computed: {
        filteredTodos() {
          if (this.filter === 'all'){
              return this.todos
          }  
           if (this.filter === 'completed'){
              return this.todos.filter(t =>t.completed)
          }
            if (this.filter === 'not-completed'){
              return this.todos.filter(t =>!t.completed)
          }
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
    TodoList, AddTodo, Loader
  }
}
</script>
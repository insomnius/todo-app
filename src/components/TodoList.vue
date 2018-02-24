<template>
  <div>
    <p></p>
    <h2 class="ui center aligned header">Insomnius learn - To Do Apps</h2>
    <hr>
    <div class="ui three column centered grid">
      <div class='column'>
        <br>
        <div class='ui basic content'>
          <div class="task">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</div>
          <p></p>
          <div class="task">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</div>
        </div>
        <br>
        <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :key="todo.key" :todo.sync="todo"></todo>
      </div>
    </div>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
      alert('Completing to do.')
    }
  }
}
</script>

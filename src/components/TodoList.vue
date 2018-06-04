<template>
  <div>
    <input type="text" v-model="currTodo" @keyup.enter="onSubmit(currTodo)">
    <button @click="onSubmit(currTodo)">添加</button>
    <ul>
      <li 
        @click="onToggleTodo(index)" 
        :class="{'done': todo.done}" 
        :key="index" 
        v-for="(todo, index) in todos">{{todo.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return ({
      todos: [],
      currTodo: ''
    })
  },

  methods: {
    onSubmit (currTodo) {
      this.todos.push({
        name: currTodo,
        done: false
      })
      this.currTodo = ''
    },

    onToggleTodo (index) {
      this.todos[index].done = !this.todos[index].done
    }
  }
}
</script>

<style>
.done {
  text-decoration: line-through;
  color: red;
}
</style>


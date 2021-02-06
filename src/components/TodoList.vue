<template>
  <input type="text" v-model="todo" placeholder="Teendő" @keyup.enter="addTodo">
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.completed">
      {{ todo.title }}
    </li>
  </ul>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const todo = ref('')
    const todos = ref([])
    let id = 0

    function addTodo () {
      todos.value.push({
        id: id,
        title: todo.value.trim(),
        completed: false
      })

      todo.value = ''
      id++
    }

    return {
      todo,
      todos,
      addTodo
    }
  }
}
</script>

<template>
  <input type="text" v-model="todo" placeholder="Teendő" @keyup.enter="addTodo">
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.completed">
      {{ todo.title }}
    </li>

    <p>Elkészült feladatok száma: {{ numberOfCompletedTodos }}</p>
  </ul>
</template>

<script>
import { computed, ref, watch } from 'vue'

export default {
  setup () {
    const todo = ref('')
    const todos = ref([])
    let id = 0

    const numberOfCompletedTodos = computed(() =>
        todos.value.filter(todo => todo.completed).length
    )

    function addTodo () {
      todos.value.push({
        id: id,
        title: todo.value.trim(),
        completed: false
      })

      todo.value = ''
      id++
    }

    watch(todos, newValue => {
      console.log(`A teendők új száma: ${newValue.length}`)
    }, { deep: true })

    return {
      todo,
      todos,
      addTodo,
      numberOfCompletedTodos
    }
  }
}
</script>

<template>
  <input type="text" v-model="todo" placeholder="Teendő">
  <p>{{ todo }}</p>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const todo = ref('')
    
    return {
      todo
    }
  }
}
</script>

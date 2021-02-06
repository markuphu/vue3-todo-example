<template>
  <input type="text" v-model="todo" placeholder="Teendő">
  {{ todo }}
</template>

<script>
export default {
  setup () {
    const todo = ''
    
    return {
      todo
    }
  }
}
</script>
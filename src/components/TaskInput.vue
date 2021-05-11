<template>
  <div class="task-input my-list">
    <input v-model="title" placeholder="Опишите задачу" type="text">
    <button @click="onAddTask" class="btn btn-outline-primary">Добавить задачу</button>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  
  setup(props, { emit }) {
    const title = ref('')
    const onAddTask = () => {
      emit('onAddTask', { title: title.value })
      title.value = ''
    }
    return {
      title,
      onAddTask
    }
  }
}
</script>

<style scoped>
.task-input {
  margin: 10px 0;
}
</style>
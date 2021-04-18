<template>
  <div class="task-input my-list">
    <input v-model="title" placeholder="Добавьте задачу" type="text" class="form-control">
    
    <button @click="onAddTask" class="btn btn-outline-primary" aria-current="page">Добавить</button>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  emits: {
    onAddTask({ title,  }) {
      if(title === '' ) {
        alert('Пожалуйста, заполните некоторую информацию!')
        return false
      }
      return true
    }
  },
  setup(props, { emit }) {
    const title = ref('')
    
    const onAddTask = () => {
      emit('onAddTask', { title: title.value})
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
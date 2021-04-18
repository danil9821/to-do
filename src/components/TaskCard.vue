<template>
  <div class="task-card my-style">
    <div>
      <h4>{{ model.title }}</h4>
    </div>
    <div>
      <button @click="emitOnDone" v-if="!model.status" class="btn btn-success">Выполнена</button>
      <button @click="emitOnRemove" v-else class="btn btn-danger">Удалить</button>
    </div>
  </div>
</template>


<script>
export default {
  emits: ['onDone', 'onRemove'],
  props: {
    model: {
      required: true,
      default: {
        id: 0,
        title: '',
        status: false
      }
    }
  },
  setup(props, { emit }) {
    const emitOnDone = () => {
      emit('onDone')
    }
    const emitOnRemove = () => {
      emit('onRemove')
    }
    return {
      emitOnDone,
      emitOnRemove
    }
  }
}
</script>

<style scoped>
.task-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
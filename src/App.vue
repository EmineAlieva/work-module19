<script>
import TodoList from './components/TodoList.vue';
export default {
  components: {
    TodoList
  }
}

</script>

<template>
  <div class="section">
    <h1>Список задач</h1>
    <TodoList/>
  </div>
</template>

<style scoped>
.section{
  max-width: 500px;
  height: 90vh;
  margin: 2rem;
  padding: 1rem;
  border: 2px solid white;
  border-radius: 1rem;
  box-shadow: 1rem 1rem  rgb(163, 214, 86, 0.8), inset 0 0 0.5rem 0.2rem greenyellow;
}
</style>

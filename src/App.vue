<script>
import TodoList from './components/TodoList.vue';
export default {
  // data() {
  //   return {
  //     tasks: []
  //   }
  // },
  // mounted() {
  //   fetch('./tasks.json')
  //     .then(response => response.json())
  //     .then(data=> {
  //       this.tasks = data.tasks;
  //       console.log('данные получены', this.tasks)
  //     })
  //     .catch(error => console.error('Error loading tasks:', error))
  // },
  // methods:{
  // },

  components: {
    TodoList
  }
}

</script>

<template>
  <div class="section">
    <h1>Список задач</h1>
    <TodoList/>
    <!-- <ul>

      <li v-for="task in tasks" :key="task.id">
        <span :class="{status: task.status }">{{ task.text }}</span>
      </li>
    </ul> -->

  </div>
</template>

<style scoped>
.section{
  max-width: 500px;
  height: 90vh;
  margin: 2rem;
  padding: 1rem;
  border: 1px solid greenyellow;
  border-radius: 1rem;
  box-shadow: 1rem 0.5rem  rgb(163, 214, 86), inset 0 0 0.5rem 0.2rem greenyellow;
}

</style>

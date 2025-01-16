<script>
import TodoItem from './TodoItem.vue';

export default {
  data(){
    return{
      tasks: [],
      newTask: ''
    }
  },
  mounted() {
    fetch('./tasks.json')
      .then(response => response.json())
      .then(data=> {
        this.tasks = data.tasks;
      })
      .catch(error => console.error('Error loading tasks:', error))
  },
  methods :{
    addTask() {
      if(this.newTask.trim() !== ''){
        this.tasks.push({
          id: Date.now(),
          text: this.newTask,
          status: false
        });
      };
      this.newTask=''
    },
    deleteTask(id){
      this.tasks = this.tasks.filter(task => task.id !== id);
      console.log(`удаление задачи${id}`)
    },
    toggleTask(id){
      const task = this.tasks.find(t => t.id === id);
      if(task) {
        task.status = !task.status;
      }
    },
    changeStatus(id){
      const task = this.tasks.find(t => t.id === id);
      if(task) {
        task.status = !task.status;
      }
    }
  },
  components: {
    TodoItem
  }
}

</script>

<template>
  <div>
    <form @submit.prevent="addTask">
      <input type="text" v-model="newTask" placeholder="Введите новую задачу" name="newTask" class="new-task">
      <input type="submit" value="Добавить задачу" class="button">
    </form>
    <ul>
      <TodoItem v-for="(task) in tasks" :key="task.id" 
        :id="task.id" :text = "task.text" :status="task.status" 
        @delete-task="deleteTask(task.id)" 
        @toggle-task="toggleTask(task.id)"
        @change-status="changeStatus(task.id)"
      />
      <li v-show="newTask.length > 0"><input type="checkbox">
        <p> {{ newTask }}</p></li>
    </ul>
  </div>
</template>


<style scoped>
ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 0;
}
li {
  font-size: 20px;
  color: green;
  border: 1px solid grey;
  border-radius: 10px;
  max-width: 600px;
  padding: 0.5rem;
  display: flex;
  justify-content: start;
}
p{
  margin: 0;
}
.new-task{
  width: 240px;
  margin: 0 10px 20px;
  border: none;
  border-bottom: 1px solid grey;
}
.new-task:focus-visible{
  outline: none;
  font-size: 14px;
}
.button {
  padding: 4px 16px;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  background: linear-gradient(150deg, rgb(212, 247, 142), rgb(87, 236, 87) 100%);
  color: rgb(82, 82, 82);
}
.button:hover{
  background: linear-gradient( 300deg, rgb(212, 247, 142), rgb(87, 236, 87));
}
</style>

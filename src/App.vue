<template>
  <div>
    <h1>The famous to-do list</h1>
     <div class="generator">
      <input class="input-task-text" type="text"  v-model="taskText" @keydown.enter="addTask">
      <button @click="addTask" class="add-task-button">
        <img style="height: 30px" src=".\assets\add_task_FILL0_wght400_GRAD0_opsz48.png" alt="Add taks button">
      </button>
  </div>

    <ProgressBar :progress="progress" />
    <TaskTable :tasks="tasks" @deleteTask="deleteTask" @doTask="doTask"/>
  </div>
</template>

<script>
import TaskTable from "./components/TaskTable.vue"
import ProgressBar from "./components/ProgressBar.vue"

export default {
  name: "App",
  components: {
    TaskTable,
    ProgressBar,
    
  },

  data() {
    return {
      taskText: '',
      tasks: [],
    };
  },
    created(){
    const json = localStorage.getItem('tasks')
    const array = JSON.parse(json)
    this.tasks = Array.isArray(array) ? array : [] 
  },

  watch:{
    tasks:{
      deep: true,
      handler(){
        localStorage.setItem('tasks', JSON.stringify(this.tasks))
      }
    }
  },
  computed: {
    progress() {
      const madeTasks = this.tasks.filter(el => el.done == true)
      return  Math.round(madeTasks.length / this.tasks.length * 100) || 0

      
    },
  },

  methods: {
    addTask() {
      if (this.taskText != "") {
        this.tasks.push({text: this.taskText, done: false})
        this.taskText = ''
      }
    },
    doTask(i){
      this.tasks[i].done = !this.tasks[i].done;
    },
    deleteTask(i){
      this.tasks.splice(i, 1)
    }
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Varela+Round&display=swap');

#app {
  font-family: 'Varela Round', sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  font-size: 50px;
  color: #212529;
}
.generator{
  display: flex;
  justify-content: center;

}
.input-task-text{
  border: none;
  width: 230px;
}
.add-task-button{
  background: #7fc2b0;
  border: none;
}
</style>

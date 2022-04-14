<template>
  <div>
    <h1>AaAaaaaaAAAAAAAA</h1>
     <div class="gerator">
      <input type="text"  v-model="taskText" @keydown.enter="addTask">
      <button @click="addTask">+</button>
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
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

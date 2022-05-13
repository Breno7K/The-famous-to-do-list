<template>
  <div class="table">
    <MyTask
      v-for="(task, i) in tasks"
      :key="task"
      :taskText="task.text"
      :doneTask="task.done"
      @doTask="$emit('doTask', i)"
      @deleteTask="$emit('deleteTask', i)"
    />
  </div>
</template>

<script>
import MyTask from "./MyTask.vue";
export default {
  components: { MyTask },

  props: {
    tasks: { type: Array },
  },
};
</script>

<style scoped>
.table {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  column-gap: 1.4vw;
  max-width: 650px;
  background: #ffd166;
  padding: 30px;
  border-radius: 50px;

  row-gap: 4vh;
  margin: 8vh auto 0 auto;
}
</style>
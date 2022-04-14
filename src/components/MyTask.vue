<template>
  <div class="task-background" :class="{'done': doneTask}" @click='$emit("doTask")'>
    <span class="close-task" @click.stop='$emit("deleteTask")'>x</span>
    <p>{{taskText}}</p>
  </div>
</template>

<script>
export default {
  props:{
    taskText: { type: String},
    doneTask: { type: Boolean}
  },
  data() {
    return {
      done: false,
    };
  },
};
</script>

<style scoped>
.task-background {
  width: 200px;
  height: 150px;
  overflow-wrap: break-word;
  word-break: normal;
  border-radius: 10%;
  background: lightsalmon;
}

.done {
  background: lightgreen;
}

.task-background p {
  width: 180px;
  text-align: left;
  margin: 20% auto 0 auto;
}
.close-task {
  background: rgb(232, 51, 51);
  width: 18px;
  line-height:50%;
  height: 18px;
  border-radius: 50%;
  cursor: context-menu;
  position: relative;
  float: right;
  right: 5%;
  top: 5%;
}
</style>
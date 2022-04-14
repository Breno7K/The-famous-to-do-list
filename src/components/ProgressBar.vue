<template>
  <div class="progress-wrapper">
      <div class="progress" :style="{width: progress + '%'}"></div>
      <h3>{{progress}}%</h3>
  </div>
</template>

<script>
export default {
    props:{
        progress:{ type: Number, default: 2 }
    }
}
</script>

<style scoped>
.progress-wrapper{
    margin: 0 auto 0 auto;
    background: lightslategray;
    width: 200px;
    height: 30px;
}
.progress-wrapper h3{
    margin: 0%;
    
}
.progress{
    background: lightgreen;
    height: 100%;

    text-align: center;
}
</style>
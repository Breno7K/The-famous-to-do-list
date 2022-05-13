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
    margin: 3vh auto 0 auto;
    background: lightslategray;
    width: 270px;;
    height: 32px;
}
.progress-wrapper h3{
    margin: 0%;
    
}
.progress{
    background: #06d6a0;
    height: 100%;

    text-align: center;
}
</style>
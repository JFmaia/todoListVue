<template>
  <div class="container">
    <span class="progess-value">{{progress}}%</span>
    <div class="task-progress">
        <div class="progress-bar" :style="{width:progress + '%'}"></div>
    </div>
  </div>
</template>

<script>
export default {
    props:{
        progress:{
            type:Number, 
            default: 0,
        }
    }
}
</script>

<style scoped>

    .container{
        width: 80%;
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
    .progess-value{
        align-self: center;
    }
    .task-progress{
        position: relative;
        height: 1px;
        border:1px solid #1d1d20;
        border-radius:8px;
    }

    .progress-bar{
        position: absolute;
        border-radius:8px;
        height: 100%;
        background-color:#580dfa;
        align-self: flex-start;
    }
</style>    
<template>
  <div class="task" :class="stateClass">
    <span @click="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{task.name}}</p>
  </div>
</template>

<script>
export default {
    props:{
        task:{
            type: Object, required:true
        }
    },
    computed:{
        stateClass(){
            return { 
                pending: this.task.pending,
                done: !this.task.pending,
            }
        }
    }
}
</script>

<style scoped>
    .task{
        position:relative;
        box-sizing: border-box;
        width: 350px;
        height: 150px;
        padding: 10px;
        border-radius: 8px;
        font-size: 2rem;
        font-weight: 400;
        cursor: pointer;
        /* tirando seleção de texto */
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .pending{
        color: #15141B;
        border-left: 12px solid #580dfa;
        background: #7437f7;
    }
    .done{
        color: #15141B;
        border-left: 12px solid #949296;
        background: #EDECEE;
        text-decoration: line-through;
    }

    .pending .close{
        background-color: #580dfa;
    }

    .done .close{
        background: #949296;
    }

    .close{
        position: absolute;
        right: 10px;
        top: 10px;
        font-size:0.9rem;
        font-weight:700;
        height: 20px;
        width: 20px;
        border-radius: 10px;
        display: flex;
        justify-content: center;
    }
</style>
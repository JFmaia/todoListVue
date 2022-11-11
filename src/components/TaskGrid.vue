<template>
    <div class="task-grid">
        <template v-if="tasks.length">
            <Task v-for="task in tasks" :key="task.name" :task="task"></Task>
        </template>
        <p v-else class="no-task">Sua vida está em <strong>dia!</strong></p>
    </div>
</template>

<script>
import Task from "./Task.vue"
export default {
    components:{Task},
    props:{
        tasks: {type:Array, required: true}
    }
}
</script>

<style scoped>
    .task-grid{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 32px;
    }

    .no-task{
        color: #EDECEE;
        font: size 1.7rem;
    }
</style>
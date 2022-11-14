<template>
  <div class="new-task">
    <input 
        v-model="name" 
        @keydown.enter="add()" 
        type="text"
        class="form-element"
        placeholder="Nova tarefa?"
    >
    <button class="form-element" @click="add()">+</button>
  </div>
</template>

<script>
export default {
    data(){
        return{
            name:''
        }
    },
    methods:{
        add(){
            this.$emit('taskAdded',{name: this.name})
            this.name = ''
        }
    }
}
</script>

<style scoped>
    .form-element{
        outline: none;
        font-size: 2rem;
        border: 2px solid #7437f7;
        padding: 5px 10px 8px;
        color: #EDECEE;
    }
    input.form-element{
        width: 500px;
        background: transparent;
        border-bottom-left-radius: 8px;
        border-top-left-radius: 8px;
    }
    button.form-element{
        border-left: none;
        background: #7437f7;
        color: #EDECEE;
        border-bottom-right-radius: 8px;
        border-top-right-radius: 8px;  
    }
</style>
<template>
	<div id="app">
		<h1>Tarefas</h1>
	<!-- Por padrão ao emitir um evento para o pai o valor já passa para a função -->
		<NewTask @taskAdded="addTask">

		</NewTask>
		<TaskGrid :tasks="tasks"/>
	</div>
</template>

<script>
import TaskGrid from "./components/TaskGrid.vue"
import NewTask from "./components/NewTask.vue";

export default {
	components:{TaskGrid, NewTask},
	data(){
		return{
			tasks:[
				{name:"Lavar louça", pending: false},
				{name:"Estudar 2hr pela manhã!", pending: true},
			]
		}
	},
	methods:{
		addTask(task){
			const sameName = t => t.name === task.name
			// Se o filter no final for 0 não os nomes não são iquais, se não, não poderá ser salvo a nova task
			const reallyNew = this.tasks.filter(sameName).length == 0
			if(reallyNew){
				this.tasks.push({
					name:task.name,
					pending:task.pending || true
				})
			}
		}
	}
}
</script>

<style>
	/* EDECEE color de textos normais */
	body {
		font-family: 'Lato', sans-serif;
		background: #15141B;
		color: #7437f7;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
		gap: 100px;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 700;
		font-size: 3rem;
	}
</style>

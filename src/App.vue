<template>
	<div class="container-todo">
		<div id="app" class="container">
			<h1>Tarefas</h1>
			<TaskProgress :progress="progress"/>
			<!-- Por padrão ao emitir um evento para o pai o valor já passa para a função -->
			<NewTask @taskAdded="addTask">

			</NewTask>
			<TaskGrid 
				:tasks="tasks" 
				@taskDeleted="deleteTask"
				@taskStateChanged="toogleTaksState"
			/>
		</div>
	</div>
	
</template>

<script>
import TaskGrid from "./components/TaskGrid.vue"
import NewTask from "./components/NewTask.vue";
import TaskProgress from "./components/TaskProgress.vue";

export default {
	components:{TaskGrid, NewTask, TaskProgress},
	data(){
		return{
			tasks:[]
		}
	},
	computed:{
		progress(){
			const total = this.tasks.length
			const done = this.tasks.filter(t=> !t.pending).length
			return Math.round(done/total*100) || 0
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
		},
		deleteTask(i){
			this.tasks.splice(i,1)
		},
		toogleTaksState(i){
			this.tasks[i].pending = !this.tasks[i].pending
		}
	}
}
</script>

<style>
	/* EDECEE color de textos normais */
	html,body{
		height: 100%;
		font-family: 'Lato', sans-serif;
		background: #15141B;
		color: #7437f7;
	}

	.container-todo{
		padding: 48px 78px;
	}

	.container{
		max-width: 1444px;
		margin: 0 auto;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		min-height: 100%;
		gap: 100px;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 700;
		font-size: 3rem;
	}
</style>

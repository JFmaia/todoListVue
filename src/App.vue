<template>
	<div id="app">
		<h1>Tarefas</h1>
		<TaskGrid :tasks="tasks"/>
	</div>
</template>

<script>
import TaskGrid from "./components/TaskGrid.vue"
export default {
	components:{TaskGrid},
	data(){
		return{
			tasks:[
				{name:"Lavar louça", pending: false},
				{name:"Estudar 2hr pela manhã!", pending: true},
			]
		}
	}
}
</script>

<style>
	/* EDECEE color de textos normais */
	body {
		font-family: 'Lato', sans-serif;
		background: #15141B;
		color: #A277FF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 700;
		font-size: 3rem;
	}
</style>

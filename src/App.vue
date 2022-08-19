<template>
	<div id="app">
		<h1>Tarefario</h1>
		<NewTask @taskAdded="addTask"/>
		<TaskGrid :tasks="tasks" />
	</div>
</template>

<script>
import NewTask from './components/NewTask.vue'
import TaskGrid from './components/TaskGrid.vue'


export default {
	components: { NewTask, TaskGrid },
	data() {
		return {
			tasks: [
				{name: 'Lavar a louça', pending: false},
				{name: 'Comprar blusa', pending: true},
				{name: 'Lavar a louça', pending: false},
				{name: 'Comprar blusa', pending: true},
			]
		}
	},
	methods: {
		addTask(task) {
			const sameName = t => t.name ===task.name
			const reallyNew = this.tasks.filter(sameName).length == 0
			if(reallyNew) {
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
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, #0e0088, #352d86, #24243e);	
		color: rgb(255, 255, 255);
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
		font-weight: 300;
		font-size: 3rem;
	}
</style>

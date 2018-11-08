<template>
	<div>
		<h1>Task List</h1>
		<ul class="todo_list">
			<li
				v-for="(task, index) in tasks"
				:key="task.id"
			>
				<div class="task_cell"><span>Name task:</span> {{ task.todo }}</div>
				<div class="task_cell"><span>Time:</span> {{ task.time }}</div>
		        <button class="delete_btn" @click="removeTask(task, index)">
		        	<i class="fas fa-trash-alt"></i>
		        </button>
			</li>
		</ul>
	</div>	
</template>


<script>
	

export default {
	name: 'TaskList',
	data() {
		return {
			tasks: [
				{
					todo: 'Write text',
					time: '20 min'
				},
				{
					todo: 'Show all tasks',
					time: '10 min'
				},
				{
					todo: 'Play cards',
					time: '15 min'
				},
			]
		}
	},
	methods: {
	    removeTask(task, index) {
	    	this.tasks.splice(index, 1);
	    },
	}
}

</script>
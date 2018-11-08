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
	}
}

</script>
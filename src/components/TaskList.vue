<template>
	<div>
		<h1>Task List</h1>
		<form @submit.prevent="addtask" class="add_task">
			<input type="text" v-model="task.name" placeholder="Our task"/>
			<input type="text" v-model="task.time" placeholder="Time task"/>
			<button type="submit" class="t-up" @click="addTask()">Add task</button>
		</form>
		<div>
			<p class="no_task" v-if="!tasks.length">No tasks!</p>
			<ul v-if="tasks.length" class="todo_list">
				<li
					v-for="(task, index) in tasks"
					:key="task.id"
				>
					<div class="task_cell"><span>Name task:</span> {{ task.name }}</div>
					<div class="task_cell"><span>Time:</span> {{ task.time }}</div>
			        <button class="delete_btn" @click="removeTask(task, index)">
			        	<i class="fas fa-trash-alt"></i>
			        </button>
				</li>
			</ul>
		</div>
	</div>	
</template>


<script>
	

export default {
	name: 'TaskList',
	data() {
		return {
			tasks: [
				{
					name: 'Write text',
					time: '20 min'
				},
				{
					name: 'Show all tasks',
					time: '10 min'
				},
				{
					name: 'Play cards',
					time: '15 min'
				},
			],
			task: {
				name: '',
				time: ''
			}
		}
	},
	methods: {
		addTask() { 
	      if (this.task.name) {
	        this.tasks.push(this.task);
	        this.task = {
	          name: '',
	          time: ''
	        }
	      }
		},
	    removeTask(task, index) {
	    	this.tasks.splice(index, 1);
	    },
	}
}

</script>
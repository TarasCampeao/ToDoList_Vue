<template>
	<div>
		<h1>ToDo List</h1>
		<form @submit.prevent="addTask" class="add_task">
			<div class="input_box">
				<input type="text" v-model="task.name" placeholder="Name task"/>
			</div>
			<div class="input_box">
				<input type="text" v-model="task.time" placeholder="Time task"/>
			</div>
			<button type="submit" class="t-up btn_add" @click="addTask()">Add task</button>
			<p class="alert" v-if="showAlert">{{ alertMessage }}</p>
		</form>
		<div v-if="tasks.length">
			<transition-group 
				name="slide"
				mode="out-in"
				class="todo_list"
				tag="ul"
				key="list"
			>
				<li
					v-for="(task, index) in tasks"
					:key="task.name"
				>
					<div class="task_cell"><span>Name task:</span> {{ task.name }}</div>
					<div class="task_cell"><span>Time:</span> {{ task.time }}</div>
			        <button class="delete_btn" @click="removeTask(task, index)">
			        	<i class="fas fa-trash-alt"></i>
			        </button>
				</li>
			</transition-group>
		</div>
		<p class="no_task" v-else>No tasks!</p>
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
			},
			showAlert: false,
			allertMessage: '',
		}
	},
	methods: {
		addTask() { 
	      if (this.task.name && this.task.time) {
	        this.tasks.push(this.task)
	        this.task = {
	          name: '',
	          time: ''
	        }
	      } else if(this.task.name =='' && this.task.time ==''){
	            this.alertMessage = "Please fill the inputs."
	            this.showAlert = true;
          }
		},
	    removeTask(task, index) {
	    	this.tasks.splice(index, 1);
	    }
	}
}

</script>
<template>
	<div>
		<h1>ToDo List</h1>
		<form @submit.prevent="addTask" class="add_task">
			<div class="input_box">
				<input type="text" v-model="task.name" placeholder="Name task"/>
			</div>
			<button :disabled="!task.name" type="submit" class="t-up btn_add" @click="addTask()">Add task</button>
		</form>
		<div v-if="tasks.length">
			<ul class="todo_list">
				<li
					v-for="(task, index) in tasks"
					:key="task.name"
					:class="{'complete': task.isCompleted}"
				>
					<div class="task_cell">
				        <button class="btn_switch" @click="changeEditing(task.name)">
				        	<i class="far fa-edit"></i>
						</button>
						<p  @click="task.isCompleted = !task.isCompleted" class="check_tsk">{{ task.name }}</p>
					</div>
					<div class="switch_text" v-if="task.isEditing">
			           <input
				           type="text"
				           v-model="editName"
				           class="edit_input"
			           >	
			           <button class="btn_change" @click="editTask(task.name)">Save change</button>
					</div>
			        <button class="delete_btn" @click="removeTask(task, index)">
			        	<i class="fas fa-trash-alt"></i>
			        </button>
				</li>
			</ul>
		</div>
		<p class="no_task" v-else>No tasks!</p>
	</div>	
</template>


<script>

export default {
	name: 'TaskList',
	data() {
		return {
			isCompleted: false,
			editName: '',
			tasks: [
				{
					name: 'Write text',
					isCompleted: false,
					isEditing: false
				},
				{
					name: 'Show all tasks',
					isCompleted: false,
					isEditing: false
				},
				{
					name: 'Play cards',
					isCompleted: false,
					isEditing: false
				},
			],
			task: {
				name: '',
			}
		}
	},
	methods: {
		addTask() { 
	      if (this.task.name !== '') {
	        this.tasks.push(this.task)
	        this.task = {
	          name: '',
	          isCompleted: false,
	          isEditing: false
	        }
	        this.task == '';
	      }
		},
	    removeTask(task, index) {
	    	this.tasks.splice(index, 1);
	    },
	    changeEditing(taskName) {
	      this.editName = taskName;
	      this.tasks = this.tasks.map(task => {
	        if(task.name === taskName) {
	          task.isEditing = !task.isEditing;
	        }
	        return task;
	      })
	    },
	    editTask(taskName) {
	      this.tasks = this.tasks.map(task => {
	        if(task.name === taskName) {
	          task.isEditing = !task.isEditing;
	          task.name = this.editName;
	        }
	        return task;
	      })
	    },
	},
}

</script>
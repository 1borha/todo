<template>
	<main>
		<h1>Task Board</h1>
		<p>Create a list of task</p>

		<div class="create-new">
			<input
				type="text"
				v-model="newTask"
				placeholder="Add a new task"
				@keypress.enter="addTask" />
			<button @click="addTask">Add</button>
		</div>

		<div class="tasks">
			<Task
				v-for="(task, i) in $store.state.tasks"
				:key="i"
				:task="task" />
		</div>

		<div class="footer">
			<button @click="clearTasks">Clear</button>
		</div>
	</main>
</template>

<script>
export default {
	name: 'IndexPage',
	data() {
		return {
			newTask: '',
		}
	},
	methods: {
		addTask() {
			if (this.newTask) {
				this.$store.commit('ADD_TASK', this.newTask);
			}
		},
		clearTasks() {
			this.$store.commit('CLEAR_TASKS');
		}
	},
}
</script>

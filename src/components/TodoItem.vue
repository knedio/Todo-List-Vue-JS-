<template>
	<div>
		<div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
			<div>
				<input type="checkbox" v-on:change="markComplete" :checked="todo.completed" />
				{{ todo.id }} - {{ todo.title }}
				<button v-on:click="$emit('update-todo',todo)" class="update-btn" v-show="!todo.completed">Update</button> 
				<button v-on:click="$emit('del-todo',todo.id)" class="del-btn">Delete</button> 
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: "TodoItem",
		props: ["todo"],
		methods: {
			markComplete() {
				this.todo.completed = !this.todo.completed;
			}
		}
	}
</script>

<style scoped>
	.todo-item {
		background: #f4f4f4;
		padding: 10px;
		border-bottom: 1px #ccc dotted;
	}
	.update-btn {
		float: right;
		padding: 5px 9px;
		margin-right: 5px;
		border-radius: 5px;
		border: none;
		background: #337ab7;
		color: #fff;
	}
	.del-btn {
		float: right;
		margin-right: 5px;
		padding: 5px 9px;
		border-radius: 5px;
		border: none;
		background: #d9534f;
		color: #fff;
	}
	.text-right {
		background: #337ab7;
		text-align: right;
	}
	.is-complete {
		text-decoration: line-through;
	}
</style>
<template>
	<div>
		<div v-bind:key="todo.id" v-for="todo in todos">
			<TodoItem 
				v-bind:todo="todo" 
				v-on:del-todo="$emit('del-todo',todo.id)" 
				v-on:update-todo="$emit('update-todo',todo)" 
			/>
		</div>
	</div>
</template>
<script>
	import TodoItem from './TodoItem';

	export default {
		name: "Todos",
		components: {
			TodoItem
		},
		props: ["todos"]
	}

</script>
<style scoped> 
	
</style>
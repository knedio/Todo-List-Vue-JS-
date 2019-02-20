<template>
	<div>
		<form v-on:submit="addTodo">
			<input type="text" name="id" v-model="id" placeholder="id" />
			<input type="text" name="title" v-model="title" placeholder="Title" />
			<input type="submit" value="Submit" class="btn" />
		</form>
		{{
			updateData
		}}
	</div>
</template>

<script>
	export default {
		name: "AddTodo",
		data() {
			return {
				id: '',
				title: '',
			}
		},
		props: ["updateData"],
		methods: {
			addTodo(e) {
				e.preventDefault();
				if (!this.id) {
					console.log('update');
					this.$emit('add-todo', this.title);
					this.title = '';
				}else{
					console.log('update');
					this.$emit('update-todo', this);
					this.id = '';
					this.title = '';
				}
			},
		},
		updated() {
			if (this.updateData.id && !this.id) {
				this.title = this.updateData.title
				this.id = this.updateData.id
			}
		}
	};
</script>

<style scoped>
	form {
		display: flex;
	}
	input[type="text"] {
		flex: 10;
		padding: 5px;
	}
	input[type="submit"] {
		flex: 2;
	}
</style>
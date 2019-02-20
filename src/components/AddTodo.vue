<template>
	<div>
		<form v-on:submit="addTodo">
			<input type="text" name="title" v-model="title" placeholder="Title" />
			<input type="submit" value="Add" v-if="!id" class="btn" />
			<input type="submit" value="Update" v-if="id" class="btn" />
		</form>
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
	      watch: { 
	      	updateData: function(newProps, oldProps) { 
	          if (newProps !== oldProps) {
		  			this.id = newProps.id;
		  			this.title = newProps.title;
		  		}
	        }
	      },
		methods: {
			addTodo(e) {
				e.preventDefault();
				if (!this.id) {
					console.log('add');
					this.$emit('add-todo', this.title);
					this.title = '';
				}else{
					console.log('update');
					this.$emit('update-todo', this);
					this.id = '';
					this.title = '';
				}
			},
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
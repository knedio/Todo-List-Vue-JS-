<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" v-on:update-todo="updateTodo" v-bind:updateData="updateTodo1" />
    <Todos 
      v-bind:todos="todos" 
      v-on:del-todo="deleteTodo"
      v-on:update-todo="updateForm"
    />
  </div>
</template>

<script>

import Header from './components/layout/Header.vue';
import Todos from './components/Todos.vue';
import AddTodo from './components/AddTodo.vue';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Text 1',
          completed: false
        },
        {
          id: 2,
          title: 'Text 2',
          completed: true
        },
        {
          id: 3,
          title: 'Text 3',
          completed: false
        }
      ],
      updateTodo1: []
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter( todo => todo.id !== id );
    },
    addTodo(title){
      const get_length = this.todos.length;
      const last_id = get_length > 0 ? this.todos[get_length-1].id : 0 ;
      const newTodo = {
        id: last_id+1,
        title,
        completed: false
      }
      this.todos = [...this.todos,newTodo]
    },
    updateForm(todo){
      this.updateTodo1 = todo;
      // console.log('test');
    },
    updateTodo(data){
      this.todos = this.todos.map(todo => {
        if (todo.id === data.id) {
          todo.title = data.title
        }
        return todo;
      })
      this.updateTodo1 = [];
      // const update = this.todo.map( todo => {
      //   if (todo.id === data.id) {
      //    todo.title = data.title;
      //   }
      //   return todo;
      // });
      // this.todo = update;
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>

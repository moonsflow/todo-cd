<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @add="addTodoItem"></TodoInput>
    <TodoList :items="todoItems" @remove="removeTodoItem"></TodoList>
    <TodoFooter @clear="clearTodoItems"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoFooter from './components/TodoFooter.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
	components: {
		TodoHeader,
		TodoFooter,
		TodoInput,
		TodoList,
	},
	data() {
		return {
			todoItems: [],
		};
	},
	methods: {
		removeTodoItem: function(value, index) {
			this.todoItems.splice(index, 1);
			localStorage.removeItem(value);
		},
		addTodoItem: function(value) {
			this.todoItems.push(value);
			localStorage.setItem(value, value);
		},
		fetchTodoItems: function() {
			for (let i = 0; i < localStorage.length; i++) {
				const item = localStorage.key(i);
				this.todoItems.push(item);
			}
		},
		clearTodoItems: function() {
			this.todoItems = [];
			localStorage.clear();
		},
	},
	created: function() {
		this.fetchTodoItems();
	},
};
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>

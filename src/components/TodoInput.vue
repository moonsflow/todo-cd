<template>
  <div>
    <input
      type="text"
      v-model="inputText"
      @keyup.enter="addTodo"
    >
    <button @click="addTodo">add</button>
  </div>
</template>

<script>
export default {
	data: function() {
		return {
			inputText: '',
		};
	},
	methods: {
		addTodo: function() {
			const value = this.inputText;
			this.$emit('add', value);
			this.clearInput();
		},
		clearInput: function() {
			this.inputText = '';
		},
	},
};
</script>

<style>
</style>
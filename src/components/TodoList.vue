<template>
  <div>
    <ul>
      <li
        v-for="(item, index) in items"
        :key="index"
      >
        {{ item }}
        <button class="button button-outline" @click="removeTodoItem(item, index)">remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
	props: ['items'],
	methods: {
		removeTodoItem: function(todoItem, index) {
			this.$emit('remove', todoItem, index);
		},
	},
};
</script>

<style>
</style>
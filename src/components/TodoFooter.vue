<template>
  <footer>
    <hr>
    <button @click="clearAllItems">Clear all</button>
  </footer>
</template>

<script>
export default {
	methods: {
		clearAllItems: function() {
			this.$emit('clear');
		},
	},
};
</script>
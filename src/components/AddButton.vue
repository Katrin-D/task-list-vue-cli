<template>
	<button class="add_btn" v-on:click="addTask()">Добавить</button>
</template>

<script>
	export default {
		methods: {
			addTask(event) {
				this.$emit('add-task', event);

			}
		}

	}
</script>

<style>	
</style>
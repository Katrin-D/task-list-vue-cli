<template>
    <div class="task_list" v-if="tasks.length !== 0">
        <div class="task" v-for="(task, index) in tasks" v-bind:key="index">
            <p v-bind:class='{done: task.completed}'>
                {{index + 1}}. {{ task.text }} {{task.index}}
            </p>
            <div>
                <button class="task_btn done_btn" v-on:click="task.completed = !task.completed">&#10004;</button>
                <button class="task_btn delete" v-on:click="deleteTask(index)">&#10799;</button>
            </div>
        </div>
    </div>
    <div v-else class="task">
        У вас пока нет задач
    </div>
</template>

<script>
export default {
    props: {
        tasks: {
            type: Object,
            completed: false,
        },
    },
    methods: {
        deleteTask(index) {
            this.$emit('delete-task', index);
        },

    }
}
</script>

<style>
</style>
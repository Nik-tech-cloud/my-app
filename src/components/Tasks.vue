<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder':' ','task']" :key="task.id" v-for="task in varTasks">
        <Task @delete-task="$emit('delete-task', task.id)" :task="task"/>
    </div>
</template>
<script>
import Task from './Task'
export default {
    name: "Tasks",
    props:  {
        varTasks: Array,
    },
    components: {
        Task
    },
    emits: ['delete-task','toggle-reminder'],
}
</script>

<style>
.task {
    margin: 0;
    background-color: rgb(173, 173, 173);
    transition: all 0.7s ease;
    padding: 0.5rem;
    display: grid;
    grid-template-columns: auto auto;
}
.task:hover {
    background-color: rgb(236, 236, 236);
}

.reminder {
    border-left: 4px solid greenyellow;
}
</style>
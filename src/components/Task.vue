<template>
<div class="txt">
<h3>{{task.title}}</h3>
<p>{{task.date}}</p>
</div>
<div class="rmv">
<button @click="deleteTask">X</button>
</div>
</template>
<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        deleteTask() {
            this.$emit('delete-task');
        }
    },
    emits: ['delete-task','toggle-reminder'],
}
</script>

<style scoped>
p, h3{
    margin: 0;
}
.txt {
    text-align: left;
}
.rmv {
    text-align: right;
}
div {
    width: 40vw;
}
button {
    background: transparent;
    border: transparent;
}
</style>
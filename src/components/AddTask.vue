<template>
    <Title text="Add a task"/>
    <div class="form-wrapper">
    <form @submit="onSubmit">
    <label for="taskName">Title:</label>
    <input type="text" v-model="taskName" name="taskName" id="taskName" placeholder="Title">
    <label for="taskDate">Date:</label>
    <input type="date" v-model="taskDate" name="taskDate" id="taskDate">
    <label for="taskReminder" id="taskReminderLbl">Reminder:</label>
    <input type="checkbox" v-model="taskReminder" name="taskReminder" id="taskReminder">
    <input type="submit" value="ADD TASK">
    </form>
    </div>
</template>
<script>
import Title from './Title.vue';
export default {
    name: 'AddTask',
    components: { Title },
    data() {
        return {
            taskName: '',
            taskDate: '2023-04-29',
            taskReminder: false,

        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();
            
            if(!this.taskName) {
                alert("Add a task!");
                return;
            }

            const tsk = {
                title: this.taskName,
                date: this.taskDate,
                reminder: this.taskReminder,
                id: Math.floor(Math.random() * 100000000)
                
            }
            this.$emit('addNewTask', tsk)

            this.taskName= '';
            this.taskDate= '';
            this.taskReminder= false;
        }
    },
    emits: ['addNewTask'],
}
</script>
<style>
.form-wrapper {
    width: 100%;
    display: flex;
    justify-content: center;
}
form {
    width: 50%;
    border: 1px solid rgb(73, 73, 73);
    border-radius: 5px;
    padding: 4rem;
}
input, label {
    display: flex;
}
input {
    justify-content: center;
    width: 98%;
}
label {
    justify-content: left;
}

#taskReminder, #taskReminderLbl {
    display: inline-block;
    width: 50%;
    text-align: left;
    margin: 0;
}
</style>
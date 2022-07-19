<template>
<div class="container">
<Title text="Simple Reminders app"/>
<Tasks @delete-task="deleteTask" @toggle-reminder="toggleReminder" :varTasks='tasks'/>
<AddTask @addNewTask="addTaskToTasks"/>
</div>
</template>

<script>
import Title from './components/Title'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Title,
    Tasks,
    AddTask
},
  data() {
    return {
      tasks: []
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        title: 'Ucenje',
        date: 'today',
        reminder: true
      },
      {
        id: 2,
        title: 'Naloga vobi',
        date: 'today',
        reminder: true
      },
      {
        id: 3,
        title: 'Igranje igric',
        date: 'today',
        reminder: false
      },
      {
        id: 4,
        title: 'Spanje',
        date: 'today',
        reminder: false
      }
    ]
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task);
    },
    addTaskToTasks(task) {
      this.tasks = [...this.tasks, task]

    }
  },

}
</script>

<style>
.container, body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

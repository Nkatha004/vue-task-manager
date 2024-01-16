<template>
    <AddTask v-if="showAddTask" @add-task = "addTask"/>
    <Tasks 
        @toggle-reminder = "toggleReminder" 
        @delete-task = "deleteTask" 
        :tasks = "tasks"
    />
</template>

<script>
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'

export default {
  name: 'Home',
  props: {
    showAddTask: Boolean
  },
  components: {
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods:{
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if(confirm("Are you sure?")){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    }, 
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id 
      ? {...task, reminder: !task.reminder} : task)
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor's appointment",
        day: "March 1st at 2:30pm",
        reminder: true
      },
      {
        id: 2,
        text: "Meeting at school",
        day: "March 3rd at 1:30pm",
        reminder: true
      },
      {
        id: 3,
        text: "Food Shopping",
        day: "March 3rd at 11:00am",
        reminder: false
      }
    ]
  }
}
</script>
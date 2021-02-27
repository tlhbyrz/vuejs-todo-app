<template>
  <main class="container">
    <Header @show-form="showForm" title="Todo List" :showAddForm="showAddForm" />
    <div v-if="showAddForm">
      <AddTask @add-task="addTask" /> 
    </div>
    <Tasks @delete-task="deleteTask" :tasks="tasks" />
  </main>
</template>

<script>
import Header from './components/Header';
import Tasks from './components/Tasks';
import AddTask from './components/AddTask';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return{
      tasks: [],
      showAddForm: false
    }
  },
  methods: {
    showForm(){
      this.showAddForm = !this.showAddForm
    },
    addTask(task){
      this.tasks = [task, ...this.tasks]
    },
    deleteTask(id){
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
  },
  created(){
    this.tasks = [
      {
        id: 1,
        text: "Vue dökümantasyonunu incele",
        date: "1st March at 2pm",
        reminder: true
      },
      {
        id: 2,
        text: "Doktor randevusu",
        date: "6st March at 8pm",
        reminder: false
      },
      {
        id: 3,
        text: "Arabayı tamire götür",
        date: "13st March at 1pm",
        reminder: true
      },
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: "Poppins", sans-serif;
}

.container{
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  padding: 0 10px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>

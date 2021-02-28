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
    async addTask(task){
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json"
        },
        body: JSON.stringify(task)
      })

      const data = await res.json();

      this.tasks = [data, ...this.tasks]
    },
    async deleteTask(id){
      const res = await fetch(`api/tasks/${id}`, {
        method: "DELETE"
      })

      if(res.status === 200){
        this.tasks = this.tasks.filter(task => task.id !== id);
      }else{
        alert("Hata oluştu!");
      }
    },
    async updateTask(id){
      const task = await this.fetchTask(id);
      const updated = { ...task, date: "3st March at 1pm" }

      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json"
        },
        body: JSON.stringify(updated)
      })

      const data = await res.json()
      this.tasks = this.tasks.map(task => task.id !== id ? task : data);
    },
    async fetchTasks(){
      const res = await fetch("api/tasks");
      const data = await res.json();

      return data;
    },
    async fetchTask(id){
      const res = await fetch(`api/tasks/${id}`);
      const data = await res.json();

      return data;
    }
  },
  async created(){
    this.tasks = await this.fetchTasks();
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

<template>
  <div id="app" class="app-container">
    <Header />
    <AddItem @addItem="handleAddItem"/>
    <TaskList 
      :todos="todos" 
      @completeItem="handleCompleteItem" 
      @deleteItem="handleDeleteItem"
    />
  </div>
</template>

<script>
import Header from './components/Header';
import TaskList from './components/TaskList';
import AddItem from './components/AddItem';
import uuid from 'uuid';

export default {
  name: 'app',
  components: {
    Header,
    TaskList,
    AddItem
  },
  data: function() {
    return {
      todos: JSON.parse(localStorage.getItem('todos')) || [{
        text: 'Do the Washing Up',
        completed: true,
        _id: uuid()
      },{
        text: 'Go for a run',
        completed: false,
        _id: uuid()
      }]
    }
  },
  methods: {
    handleAddItem(newText) {
      const newTodo = {
        text: newText,
        completed: false,
        _id: uuid()
      }
      this.todos.push(newTodo);
    },
    handleCompleteItem(_id) {
      for (let i = 0; i < this.todos.length; i++) {
        if (this.todos[i]._id === _id) {
          this.todos[i].completed = !this.todos[i].completed;
          break;
        }
      }
    },
    handleDeleteItem(_id) {
      this.todos = this.todos.filter(todo => todo._id !== _id);
    }
  },
  created() {

  },
  updated() {
    localStorage.setItem('todos', JSON.stringify(this.todos));
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  height: 100vh;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
.app-container {
  height: 100%;

  overflow: auto;

  background: rgb(0,215,222);
  background: linear-gradient(185deg, rgba(0,215,222,1) 0%, rgba(2,158,196,1) 52%, rgba(1,89,232,1) 100%);
}
</style>

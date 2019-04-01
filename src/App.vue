<template>
  <div id="app">
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
      todos: [{
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
  mounted() {

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <h1 class="title">Vue 3 Todo App</h1>
  <form @submit.prevent="addNewTodo">
    <label>New Todo</label>
    <input v-model="newTodo" name="newTodo"/>
    <button>Add New Todo</button>
  </form>
  <div class="allDone" @click="allDone"><button>Mark All Done</button></div>
  <ul class="grid">
    <li v-for="todo in todos" v-bind:key="todo.id" class="todo">
      <h3 v-bind:class="{done: todo.done}" @click="toggleDone(todo)">{{ todo.content }}</h3>
      <button @click="removeItem(todo)" class="remove">Remove item</button>
    </li>
  </ul>
</template>

<script>
import { ref } from 'vue';

export default {
  setup(){

    const newTodo = ref('');
    const todos = ref([]);

    function addNewTodo(){
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newTodo.value
      });
      newTodo.value = '';
    }

    function toggleDone(todo){
      todo.done = !todo.done;
    }

    function removeItem(todo){
        todos.value.shift(todo);
      }

    function allDone(){
      todos.value.forEach((
        todo) => todo.done = true
      )
    }

    return {
      addNewTodo,
      newTodo,
      todos,
      toggleDone,
      removeItem,
      allDone

    }
  }
  }
</script>

<style>
body {
  font-family: sans-serif;
  padding-top: 1em;
  padding-bottom: 1rem;
  font-size: 2em;
  width: 80%;
  margin: 0 auto;
}
input, textarea, button, p, div, section, article, select {
  display: 'block';
  width: 100%;
  font-family: sans-serif;
  font-size: 1em;
  margin: 0.5em;
}
.todo {
  cursor: pointer;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
}

.done {
  text-decoration: line-through;
}
li{
  list-style-type: none;
  }
.done {
  text-decoration: line-through;
}
.remove {
  width: 100px;
  display: flex;
  font-size: 1.5rem;
  align-content: space-around;
}
.allDone{
  display: grid;
  justify-content: center;
  margin-right: 50px;
}
.title {
  color: lightgreen;
  display: flex;
  justify-content: center;
  }
</style>
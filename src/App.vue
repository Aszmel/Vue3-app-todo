<template>
  <h1>Vue 3 Todo App</h1>
  <form @submit.prevent="addNewTodo">
    <label>New Todo</label>
    <input v-model="newTodo" name="newTodo"/>
    <button>Add New Todo</button>
  </form>
  <h2>{{newTodo}}</h2>
</template>

<script>
import { ref } from 'vue';

export default {
  setup(){

    const newTodo = ref('');

    function addNewTodo(){
      console.log("New Todo Added");
      console.log("newTodo ref is " + newTodo.value);
    }

    return {
      addNewTodo,
      newTodo,
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
.done {
  text-decoration: line-through;
}
</style>
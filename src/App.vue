<script setup>
import TodoItem from "@/components/TodoItem.vue";
import TodoForm from "@/components/TodoForm.vue";
import {ref} from "vue";
import uniqueId from "lodash.uniqueid";

const toDoItems = ref([
  {id: uniqueId("todo-"), label: "Learn Vue", done: false},
  {id: uniqueId("todo-"), label: "Having Fun with MAUI", done: true},
  {id: uniqueId("todo-"), label: "Finish CTF Project", done: false},
]);

function addToDo(todoLabel) {
  toDoItems.value.push({id: uniqueId("todo-"), label: todoLabel, done: false});
  console.log("To-do added", todoLabel);
}

</script>

<template>
  <div>
    <h1>My Todo List</h1>
    <todo-form @todo-added="addToDo"></todo-form>
    <div v-for="todo in toDoItems" :key="todo.id">
      <todo-item :id="todo.id" :todo="todo" :label="todo.label" :done="todo.done"></todo-item>
    </div>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

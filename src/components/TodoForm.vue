<script setup>

import {getCurrentInstance, ref} from "vue";

const instance = getCurrentInstance();
const label = ref('');


const handleSubmit = (e) => {
  e.preventDefault();
  if (label.value === '') {
    return
  }
  instance.emit('todo-added', label.value)
}

</script>

<template>
  <form @submit.prevent="handleSubmit">
    <label for="new-todo-input">What needs to be done? </label>
    <input
        type="text"
        id="new-todo-input"
        placeholder="What needs to be done."
        autocomplete="off"
        v-model="label"
    />
    <button type="submit">Add</button>
    <p>Message : {{label}}</p>
  </form>
</template>

<style scoped>

</style>
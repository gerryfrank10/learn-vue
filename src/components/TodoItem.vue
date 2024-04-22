<script setup>
import {onMounted, ref} from "vue";
import uniqueId from "lodash.uniqueid";

const props = defineProps({
  label: {
    type: String,
    required: true
  },
  done: {
    type: Boolean,
    default: false,
  },
})
const id = ref('')
const isDone = ref(props.done);
onMounted(() => {
  id.value = uniqueId("todo-item-");
})
</script>

<template>
  <div>
    <input type="checkbox" :id="id" :checked="isDone" />
    <label :for="id" class="label">{{ label }}</label>
  </div>
</template>

<style scoped>

</style>
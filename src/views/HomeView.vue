<template>
  <main>
    <AddToDo @add-todo="addToDo" />
    <ToDoList items="items"/>
  </main>
</template>

<script setup>
import AddToDo from "@/components/AddToDo.vue";
import ToDoList from "@/components/ToDoList.vue";

import { ref } from "vue";

const items = ref([]);
function addToDo(text) {
  items.value.push(text);
}
</script>

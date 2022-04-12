<template>
  <main>
    <div class="container">
      <div class="row d-flex justify-content-center">
        <div class="col-12 col-lg-8 col-xl-6 pt-5">
          <AddToDo @add-todo="addToDo" />
          <ToDoList class="mt-2" :items="items" />
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
import AddToDo from "@/components/AddToDo.vue";
import ToDoList from "@/components/ToDoList.vue";

import { ref } from "vue";

const items = ref([]);
function addToDo(item) {
  items.value.push(item);
}
</script>

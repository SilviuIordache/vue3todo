<template>
  <main>
    <div class="container">
      <div class="row d-flex justify-content-center">
        <div class="col-12 col-lg-8 col-xl-6 pt-5">
          <AddToDo @add-todo="addToDo" />
          <ToDoList
            @toggle-completion="toggleCompletion"
            @delete-item="deleteItem"
            class="mt-2"
            :items="items"
          />
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

  const storage = localStorage.getItem("toDoItems");
  if (storage) {
    const newItems = JSON.parse(storage);
    newItems.push(item);
    updateStorage(newItems);
  } else {
    const newItems = [];
    newItems.push(item);
    updateStorage(newItems);
  }
}

function toggleCompletion(id) {
  const arrayID = items.value.findIndex((item) => item.id === id);
  items.value[arrayID].completed = !items.value[arrayID].completed;
  updateStorage(items.value);
}

function deleteItem(id) {
  const arrayID = items.value.findIndex((item) => item.id === id);
  items.value.splice(arrayID, 1);
  updateStorage(items.value);
}

function updateStorage(items) {
  localStorage.setItem("toDoItems", JSON.stringify(items));
}
</script>

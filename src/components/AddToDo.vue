<template>
  <div class="card px-3 py-5">
    <div class="card-body">
      <h1 class="mb-5">Add to do</h1>
      <form @submit.prevent="addGoal">
        <div>
          <label for="addToDo" class="form-label">Description</label>
          <input
            v-model="toDo"
            type="text"
            class="form-control"
            id="addToDo"
            placeholder="a task..."
          />
        </div>
        <div class="mt-3">
          <p>Priority</p>
          <p>{{ priority }}</p>
          <div class="d-flex">
            <button
              type="button"
              class="btn btn-secondary"
              :disabled="decrementDisabled"
              @click="decrementPrio"
            >
              -
            </button>
            <button
              type="button"
              class="btn btn-secondary ms-1"
              :disabled="incrementDisabled"
              @click="incrementPrio"
            >
              +
            </button>
          </div>
        </div>
        <button
          type="submit"
          class="btn btn-primary mt-4"
          :disabled="addGoalDisabled"
        >
          Add
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, computed } from "vue";
const emit = defineEmits(["add-todo"]);

const toDo = ref("");
let addGoalDisabled = ref(true);
watch(toDo, (val) => {
  addGoalDisabled.value = val.length < 1 ? true : false;
});

function addGoal() {
  const payload = {
    text: toDo.value,
    prio: priority.value,
  };
  emit("add-todo", payload);
  toDo.value = "";
  priority.value = 1;
}

const priority = ref(1);
const incrementDisabled = computed(() => {
  return priority.value === 4;
});
function incrementPrio() {
  priority.value++;
}
const decrementDisabled = computed(() => {
  return priority.value === 0;
});
function decrementPrio() {
  priority.value--;
}
</script>

<style scoped></style>

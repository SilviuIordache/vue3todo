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

<script>
import { ref, watch, computed } from "vue";

export default {
  setup(_, context) {
    const toDo = ref("");
    let addGoalDisabled = ref(true);
    watch(toDo, (val) => {
      addGoalDisabled.value = val.length < 1 ? true : false;
    });

    function addGoal() {
      context.emit("add-todo", toDo.value);
      toDo.value = "";
    }

    const priority = ref(0);

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

    return {
      toDo,
      addGoal,
      addGoalDisabled,
      priority,
      incrementDisabled,
      incrementPrio,
      decrementDisabled,
      decrementPrio,
    };
  },
};
</script>

<style scoped></style>

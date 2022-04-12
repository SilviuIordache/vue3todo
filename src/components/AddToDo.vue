<template>
  <div class="card px-3 py-5">
    <div class="card-body">
      <h1 class="mb-5">Add to do</h1>
      <form @submit.prevent="addGoal">
        <label for="addToDo" class="form-label">New to do</label>
        <input
          v-model="toDo"
          type="text"
          class="form-control"
          id="addToDo"
          placeholder="a task..."
        />
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
import { ref, watch } from "vue";

export default {
  setup(_, context) {
    const toDo = ref("");
    let addGoalDisabled = ref(true);

    watch(toDo, (val) => {
      addGoalDisabled.value = val.length < 1 ? true : false;
    });

    function addGoal() {
      context.emit("add-todo", toDo.value)
    }

    return {
      toDo,
      addGoal,
      addGoalDisabled,
    };
  },
};
</script>

<style scoped></style>

<template lang="">
  <div class="card px-3 py-5">
    <div class="card-body">
      <h1 class="mb-3">List items: {{ props.items.length }}</h1>
      <div v-if="props.items.length > 0">
        <div
          v-for="(item, index) in props.items"
          :key="index"
          class="d-flex align-items-center"
        >
          <input
            :checked="item.completed"
            type="checkbox"
            @click="toggleCompletion(item.id)"
            class="me-2"
          />
          <div :class="{ line: item.completed }">
            {{ index + 1 }}. {{ item.text }} | prio: {{ item.prio }}
          </div>
        </div>
      </div>
      <p v-else>No items added yet</p>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(["toggle-completion"]);
const props = defineProps({ items: Array });

function toggleCompletion(id) {
  emit("toggle-completion", id);
}
</script>
<style>
.line {
  text-decoration: line-through;
}
</style>

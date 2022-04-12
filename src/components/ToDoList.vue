<template lang="">
  <div class="card px-3 py-5">
    <div class="card-body">
      <h1 class="mb-3">List items: {{ props.items.length }}</h1>
      <div v-if="props.items.length > 0">
        <div v-for="(item, index) in props.items" :key="index">
          <input type="checkbox" @click="toggleCompletion">
          {{ index + 1 }}. {{ item.text }} | prio: {{ item.prio }}
        </div>
      </div>
      <p v-else>No items added yet</p>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(["toggleCompletion"]);
const props = defineProps({ items: Array });

function toggleCompletion() {
  
}
</script>
<style lang=""></style>

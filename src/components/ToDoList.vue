<template lang="">
  <div class="card px-3 py-5">
    <div class="card-body">
      <div v-for="(item, index) in props.items" :key="index">
        {{ index + 1 }}. {{ item }}
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({ items: Array });
</script>
<style lang=""></style>

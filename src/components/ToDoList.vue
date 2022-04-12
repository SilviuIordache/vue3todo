<template lang="">
  <div class="card px-3 py-5">
    <div class="card-body">
      <div v-for="(item, index) in items" :key="index">
        {{ index + 1 }}. {{ item }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["items"],
};
</script>
<style lang=""></style>

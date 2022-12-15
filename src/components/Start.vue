<template>
  <div
    id="start"
    @click="$emit('start')">
    <img
      src="../assets/IAG_White.png"
      alt="" />
    <h1>Touch here to start system</h1>
  </div>
</template>

<script setup>
  const emit = defineEmits(['start'])
</script>

<style scoped>
  #start {
    height: 100%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background: var(--IAG-purple);
  }
  img {
    width: 100%;
    height: auto;
    margin: auto;
  }
  h1 {
    width: 100%;
    margin-top: auto;
    margin-bottom: 1em;
    text-align: center;
  }
</style>

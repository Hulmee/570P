<template>
  <div
    id="TSW-570P"
    class="">
    <Start
      v-if="startFB"
      @start="startFB = !startFB" />
    <Main
      v-else
      @Off="startFB = !startFB" />
  </div>
</template>

<script setup>
  import { ref } from '@vue/reactivity'
  import Start from './components/Start.vue'
  import Main from './components/Main.vue'

  const startFB = ref(false)

  const start = () => {
    console.log('start touched')
  }
</script>

<style scoped>
  #TSW-570P {
    height: 100%;
    width: 100%;
  }
  @media (min-width: 365px) {
    #TSW-570P {
      height: 640px;
      width: 360px;
      position: relative;
      top: -30px;
      /* left: 2px; */
      /* border-radius: 2em; */
    }
  }
</style>

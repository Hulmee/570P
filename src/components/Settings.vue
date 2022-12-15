<template>
  <div
    id="settings"
    class="">
    <h2>Select System type</h2>
    <div class="btn-wrap">
      <div
        @click="$emit('IPTV')"
        class="btn-rnd"
        :class="{ active: syst == 2 }">
        <font-awesome-icon
          icon="fa-solid fa-tv"
          size="2x" />
      </div>
      <h2>IPTV</h2>
    </div>
    <div class="btn-wrap">
      <div
        @click="$emit('Pres')"
        class="btn-rnd"
        :class="{ active: syst == 1 }">
        <font-awesome-icon
          icon="fa-solid fa-person-chalkboard"
          size="2x" />
      </div>
      <h2>Presention</h2>
    </div>
  </div>
</template>

<script setup>
  const props = defineProps({
      syst: Number,
    }),
    emit = defineEmits(['IPTV', 'Pres'])
</script>

<style scoped>
  #settings {
    height: 100%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    flex-direction: column;
    z-index: 2;
  }
  .btn-wrap {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
  }
  .btn-wrap > h2 {
    width: 50%;
    text-align: center;
  }
</style>

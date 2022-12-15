<template>
  <section id="TV">
    <!-- <div
      v-for="i of 10"
      :key="i"
      class="btn-sqr">
      <img
        src="@/assets/Images/TV-Logos/7.svg"
        alt="" />
    </div> -->
    <IPTVbtn
      v-for="btn in 30"
      :key="btn"
      :num="btn" />
  </section>
</template>

<script setup>
  import IPTVbtn from './IPTVbtn.vue'
</script>

<style scoped>
  #TV {
    height: 100%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    /* flex-direction: column; */
    flex-wrap: wrap;
    overflow: auto;
  }
</style>

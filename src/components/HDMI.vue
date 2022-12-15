<template>
  <section
    id="HDMI"
    class="">
    <h1 class="text">Plug your device into HDMI cable</h1>
    <div class="icons">
      <font-awesome-icon
        class="icons"
        icon="fa-solid fa-mobile-screen" />
      <font-awesome-icon
        class="icons"
        icon="fa-solid fa-laptop" />
      <font-awesome-icon
        class="icons"
        icon="fa-solid fa-computer" />
    </div>
  </section>
</template>

<script setup>
  //
</script>

<style scoped>
  #HDMI {
    height: 100%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  .text {
    font-size: 2em;
    text-align: center;
  }
  .icons {
    padding: 1em;
    height: 3em;
  }
  .icons {
    color: var(--IAG-Yellow);
  }
</style>

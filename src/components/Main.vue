<template>
  <div
    id="main"
    class="">
    <nav>
      <p
        id="time"
        class="nav-text">
        12:00 PM
      </p>
      <p
        id="room"
        class="nav-text">
        Room Name
      </p>
      <div id="pwr-con">
        <div
          id="pwr"
          class="btn-rnd btn-rnd-sm"
          @click="$emit('Off')">
          <font-awesome-icon icon="fa-solid fa-power-off" />
        </div>
      </div>
    </nav>
    <HDMI v-if="HDMIshow" />
    <IPTV v-else />
    <footer>
      <div
        class="btn-rnd btn-rnd-sm"
        @click="volDwn">
        <font-awesome-icon icon="fa-solid fa-volume-low" />
      </div>
      <progress
        :value="volVal"
        max="100"></progress>
      <div
        class="btn-rnd btn-rnd-sm"
        @click="volUp">
        <font-awesome-icon icon="fa-solid fa-volume-high" />
      </div>
    </footer>
  </div>
</template>

<script setup>
  import { ref } from '@vue/reactivity'
  import HDMI from './HDMI.vue'
  import IPTV from './IPTV.vue'

  const emit = defineEmits(['Off'])
  const volVal = ref(50),
    HDMIshow = ref(false),
    volUp = () => {
      volVal.value++
    },
    volDwn = () => {
      volVal.value--
    }
</script>

<style scoped>
  * {
    --prg-height: 0.25em;
  }
  progress[value] {
    -webkit-appearance: none;
    appearance: none;
    width: 50%;
    height: 2em;
  }

  progress[value]::-webkit-progress-bar {
    background-color: #fff;
    border-radius: 0.5em;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.25) inset;
  }
  progress[value]::-webkit-progress-value {
    border-radius: 0.5em;
    background-color: var(--IAG-blue);
  }
  #main {
    height: 100%;
    width: 100%;
    background: var(--dark);
    display: flex;
    align-items: center;
    /* justify-content: center; */
    justify-content: space-between;

    flex-direction: column;
  }

  nav,
  footer {
    height: 4em;
    width: 100%;
    background: var(--IAG-purple);
    /* height: 100%; */
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  #pwr {
    /* margin-left: auto; */
    background: linear-gradient(145deg, #ff6669, #d95658);
  }
  .nav-text {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  #room {
    flex-grow: 3;
    text-align: center;
  }
  #time,
  #pwr-con {
    flex-grow: 1;
    /* padding-left: 0.5em; */
  }
  #pwr-con {
    /* padding-left: auto; */
    display: flex;
    justify-content: flex-end;
  }
</style>

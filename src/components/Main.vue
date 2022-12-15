<template>
  <div
    id="main"
    class="">
    <nav>
      <div
        @click="SetShow = !SetShow"
        id="set-btn"
        class="settings">
        <div
          class="btn-rnd btn-rnd-sm"
          :class="{ success: SetShow }">
          <font-awesome-icon icon="fa-solid fa-gears" />
        </div>
      </div>
      <div id="room">
        <p class="nav-text">Room Name</p>
        <p class="nav-text">12:00 PM</p>
      </div>
      <div id="pwr-con">
        <div
          id="pwr"
          class="btn-rnd btn-rnd-sm"
          @click="$emit('Off')">
          <font-awesome-icon icon="fa-solid fa-power-off" />
        </div>
      </div>
    </nav>
    <div
      class="center"
      v-if="SetShow">
      <Settings
        :syst="subPage"
        @IPTV="subPage = 2"
        @Pres="subPage = 1" />
    </div>
    <div
      class="center"
      v-else>
      <HDMI v-if="subPage == 1" />
      <IPTV v-if="subPage == 2" />
    </div>
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
  import Settings from './Settings.vue'

  const emit = defineEmits(['Off'])
  const volVal = ref(50),
    SetShow = ref(false),
    subPage = ref(2),
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
  #set-btn,
  #pwr-con {
    flex-grow: 1;
    /* padding-left: 0.5em; */
  }
  #pwr-con {
    /* padding-left: auto; */
    display: flex;
    justify-content: flex-end;
  }
  .center {
    overflow: auto;
    height: 100%;
    width: 100%;
  }
</style>

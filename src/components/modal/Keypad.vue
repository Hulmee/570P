<template>
  <teleport to="#TSW-570P">
    <section class="modal col">
      <div class="k-info">
        <h3><small> Enter Passcode to unlock</small></h3>
      </div>

      <div class="keypad">
        <div
          id="passW"
          class="">
          <input
            class="bdr"
            type="password"
            v-model="passcodeString" />
          <h2 class="error">
            <span v-show="error"> Incorect Pin </span>
          </h2>
        </div>

        <div
          v-for="i of 9"
          :key="i"
          class="b-con"
          :style="`grid-area: b${i}`">
          <div
            @click="keyPress(i)"
            class="btn-rnd btn-rnd-sm">
            {{ i }}
          </div>
        </div>
        <div
          class="b-con"
          style="grid-area: b10">
          <div
            @click="keyPress(0)"
            class="btn-rnd btn-rnd-sm">
            0
          </div>
        </div>
        <div
          class="b-con"
          style="grid-area: y">
          <div
            @click="evalPin(passcodeString)"
            class="btn-rnd btn-rnd-sm"
            style="background: var(--IAG-green)">
            <font-awesome-icon icon="fa-solid fa-check" />
          </div>
        </div>
        <div
          class="b-con"
          style="grid-area: n">
          <div
            @click="clearPin"
            class="btn-rnd btn-rnd-sm"
            style="background: var(--IAG-red)">
            <font-awesome-icon icon="fa-solid fa-xmark" />
          </div>
        </div>
      </div>
    </section>
  </teleport>
</template>

<script setup>
  import { ref } from '@vue/reactivity'

  const passcode = ref([]),
    passcodeString = ref(''),
    error = ref(false),
    pinTimeout = ref(null),
    corectPin = ref('1988')

  const keyPress = e => {
      error.value = false
      passcode.value.push(e)
      passcodeString.value = passcode.value.join('')
    },
    evalPin = Pin => {
      if (Pin === corectPin.value) {
        emits('sucess')
        passcode.value = []
        passcodeString.value = ''
      } else {
        error.value = true
        passcode.value = []
        passcodeString.value = ''
      }
    },
    clearPin = () => {
      error.value = false
      passcode.value = []
      passcodeString.value = ''
    }

  const emits = defineEmits(['sucess'])
</script>

<style scoped>
  .modal {
    background: var(--IAG-purple);
  }
  .k-info {
    padding: 0.5em;
    background-color: var(--dark);
    text-align: center;
    border: 10px solid var(--dark);
    border-radius: 20px;
    box-shadow: inset 5px 5px 10px var(--light2),
      inset -5px -5px 10px var(--light2);
    background: var(--dark);
    border-radius: 25px;
  }
  .k-info > h3 {
    padding: 1em;
    max-width: 300px;
    text-align: center;
  }

  .keypad {
    height: 75%;
    width: 90%;
    margin-top: 1rem;
    background-color: var(--dark);
    text-align: center;
    border: 10px solid var(--dark);
    border-radius: 20px;
    box-shadow: inset 5px 5px 10px var(--light2),
      inset -5px -5px 10px var(--light2);
    display: grid;
    grid-template-areas:
      'pass pass pass'
      'b1 b2 b3'
      'b4 b5 b6'
      'b7 b8 b9'
      'y b10 n';
  }

  .col {
    flex-direction: column;
  }
  .error {
    color: var(--IAG-red);
    height: 2em;
    width: 100%;
    padding: 0.25em;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .error > span {
    width: 100%;
  }
  #passW {
    height: 1em;
    grid-area: pass;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100%;
  }
  .b-con {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>

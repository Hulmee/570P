<template>
  <teleport to="#TSW-570P">
    <section
      class="modal"
      @click="$emit('cancel')">
      <div class="card">
        <h3 class="title">
          Lock Control Panel
          <br />
          <small>Are you sure you want to lock the panel?</small>
        </h3>

        <div class="content container">
          <p>Lock</p>
          <div
            class="btn-rnd btn-rnd-sm"
            @click="$emit('lock')">
            <font-awesome-icon icon="fa-solid fa-lock" />
          </div>
        </div>

        <div class="canel">
          <!-- <div> -->
          <p>Cancel</p>
          <div
            class="btn-rnd btn-rnd-sm"
            @click="$emit('cancel')">
            <font-awesome-icon icon="fa-solid fa-lock-open" />
          </div>
          <!-- </div> -->
        </div>
      </div>
    </section>
  </teleport>
</template>

<script setup>
  const emit = defineEmits(['lock', 'cancel'])
</script>

<style>
  span {
    width: 2em;
  }
  .card {
    max-height: 300px;
    height: 50%;
    background-color: var(--dark);
    text-align: center;
    border: 10px solid var(--dark);
    border-radius: 20px;
    box-shadow: inset 5px 5px 10px var(--light2),
      inset -5px -5px 10px var(--light2);
    transition: 0.5s;
    display: grid;
    grid-template-areas:
      'title title'
      'cont can';
  }

  .title {
    color: var(--light);
    grid-area: title;

    padding: 10px;
    margin: 5px 20px;
    border-radius: 8px;
  }

  .content {
    grid-area: cont;
    display: flex;
    flex-direction: column;
    align-items: conter;
    justify-content: center;
    color: var(--light);
    margin-bottom: 1em;
  }

  .canel {
    grid-area: can;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: var(--light);
    margin-bottom: 1em;
  }
</style>

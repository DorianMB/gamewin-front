<template>
  <div class="container">
    <div>
      <h1 class="title">
        GameWin
        <font-awesome-icon :icon="['far', 'address-card']" />
      </h1>
      <div class="links">
        <button
          class="button--green"
        >
          Add data
        </button>
        <button
          class="button--grey"
        >
          GitHub
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 98vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.button--green, .button--grey {
  background: white;
}

.links {
  padding-top: 15px;
}
</style>

<template>
  <div class="bet-container">
    <bet-item v-for="match in matchs" :match="match"></bet-item>
  </div>
</template>

<script>
import BetItem from "../components/BetItem";

export default {
  name: "bet",
  components: {BetItem},
  data: () => {
    return {
      matchs: null,
    }
  },
  beforeMount() {
    this.update();
  },
  methods: {
    update() {
      if (localStorage.matchs) {
        this.matchs = JSON.parse(localStorage.matchs)
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .bet-container {
    padding: 3rem 1rem;
  }
</style>

<template>
  <div class="bet-container">
    <bet-item :bet="bet"></bet-item>
  </div>
</template>

<script>
import BetItem from "../components/BetItem";
export default {
  name: "bet",
  components: {BetItem},
  data: () => {
    return {
      bet: {
        date: new Date(),
        competition: 'compétition 1',
        game: 'League of Legends',
        teams: ['G2', 'SKT'],
        ratings: [21, 10, 1],
        numberOfBets: 10
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

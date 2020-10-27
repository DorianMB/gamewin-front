<template>
  <div class="bet-container">
    <bet-item v-for="bet in bets" :bet="bet"></bet-item>
  </div>
</template>

<script>
import BetItem from "../components/BetItem";

export default {
  name: "bet",
  components: {BetItem},
  data: () => {
    return {
      bets: [
        {
          date: new Date(),
          competition: 'compétition 1',
          game: 'League of Legends',
          teams: ['G2', 'SKT'],
          ratings: [21, 10, 1],
          numberOfBets: 45
        },
        {
          date: new Date(),
          competition: 'compétition 1',
          game: 'League of Legends',
          teams: ['G2', 'SKT'],
          ratings: [10, 4, 14],
          numberOfBets: 30
        },
        {
          date: new Date(),
          competition: 'compétition 2',
          game: 'League of Legends',
          teams: ['G2', 'SKT'],
          ratings: [22, 8, 2],
          numberOfBets: 100
        },
      ]
    }
  }
}
</script>

<style scoped lang="scss">
  .bet-container {
    padding: 3rem 1rem;
  }
</style>

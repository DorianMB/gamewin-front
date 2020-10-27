<template>
  <div v-if="bet" class="bet-item d-flex justify-content-between">
    <div class="d-flex flex-column justify-content-around">
      <span class="bet-header">{{ formatDate(bet.date) }} - {{ bet.competition }}</span>
      <span class="teams">{{ bet.teams[0] }} - {{ bet.teams[1] }}</span>
    </div>
    <div class="d-flex">
      <div class="rating-card d-flex flex-column">
        <span class="rating-team">{{ bet.teams[0] }}</span>
        <span class="rating">{{ bet.ratings[0] }}</span>
      </div>
      <div class="rating-card d-flex flex-column">
        <span class="rating-team">Draw</span>
        <span class="rating">{{ bet.ratings[1] }}</span>
      </div>
      <div class="rating-card d-flex flex-column">
        <span class="rating-team">{{ bet.teams[1] }}</span>
        <span class="rating">{{ bet.ratings[2] }}</span>
      </div>
      <div class="bet-link d-flex align-items-center">
        <div class="d-flex flex-column align-items-center">
          <span><strong>{{bet.numberOfBets}}</strong></span>
          <span>pari(s)</span>
        </div>
        <font-awesome-icon :icon="['fas', 'chevron-right']" />
      </div>
    </div>
  </div>
</template>

<script>
import * as moment from "moment";

export default {
  name: "Bet-Item",
  props: {
    bet: {
      date: Date,
      competition: String,
      game: String,
      teams: Array,
      ratings: Array,
      numberOfBets: Number
    }
  },
  methods: {
    formatDate(date) {
      moment.locale('fr');
      const format = 'dddd Do MMMM YYYY, HH:mm';
      if (date) {
        return moment(date).format(format);
      } else {
        return moment(new Date()).format(format);
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .bet-item {
    margin: 1rem 0;
    border: 1px solid #cdcdcd;
    border-radius: 5px;
    padding: 0.5rem;

    .bet-header {
      color: #cdcdcd;
      font-size: 11px;
    }

    .rating-card {
      background: #ffed4c;
      width: 8vw;
      padding: 0.25rem 1rem;
      border-radius: 5px;
      margin: 0 0.5rem;

      .rating-team {
        font-size: 11px;
        text-transform: uppercase;
      }

      .rating {
        font-weight: bold;
      }
    }

    .bet-link {
      font-size: 12px;
      svg {
        color: gray;
        margin-left: 5px;
        font-size: 14px;
      }
    }
  }
</style>

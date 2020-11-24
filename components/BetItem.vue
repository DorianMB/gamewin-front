<template>
  <button v-if="match" class="btn btn-block text-left bet-item d-flex justify-content-between align-items-center">
    <div class="d-flex flex-column">
      <span class="bet-header">{{ formatDate(match.date) }} - {{ match.competition }}</span>
      <span class="teams">{{ match.teams[0] }} - {{ match.teams[1] }}</span>
    </div>
    <div class="d-flex">
      <button class="btn rating-card d-flex flex-column" :class="isChosen(0)" v-on:click="addBet(0, match)">
        <span class="rating-team">{{ match.teams[0] }}</span>
        <span class="rating">{{ match.ratings[0] }}</span>
      </button>
      <button class="btn rating-card d-flex flex-column" :class="isChosen(1)" v-on:click="addBet(1, match)">
        <span class="rating-team">Draw</span>
        <span class="rating">{{ match.ratings[1] }}</span>
      </button>
      <button class="btn rating-card d-flex flex-column" :class="isChosen(2)" v-on:click="addBet(2, match)">
        <span class="rating-team">{{ match.teams[1] }}</span>
        <span class="rating">{{ match.ratings[2] }}</span>
      </button>
      <div class="bet-link d-flex align-items-center">
        <div class="d-flex flex-column align-items-center">
          <span><strong>{{match.numberOfBets}}</strong></span>
          <span>pari(s)</span>
        </div>
        <font-awesome-icon :icon="['fas', 'chevron-right']"/>
      </div>
    </div>
  </button>
</template>

<script>
import * as moment from "moment";

export default {
  name: "Bet-Item",
  data: () => {
    return {
      bet: {
        matchId: null,
        choice: null,
        price: null,
      },
    }
  },
  props: {
    match: {
      date: Date,
      competition: String,
      game: String,
      teams: Array,
      ratings: Array,
      numberOfBets: Number
    },
    bets: Array
  },
  mounted() {
    this.getBets()
  },
  watch: {
    match: function(newVal, oldVal) { // watch it
      this.getBets();
    }
  },
  methods: {
    getBets() {
      if (localStorage.bets) {
        this.bets = JSON.parse(localStorage.bets);
        if (this.bets) {
          this.bet = this.bets.find(b => {
            return b.matchId === this.match.id;
          });
        }
      }
    },
    addBet(choice, match) {
      this.getBets();
      let newBets = [];
      if (this.bets) {
        newBets = this.bets.filter(b => {
          return b.matchId !== match.id
        });
      }
      this.bet = {
        matchId: match.id,
        choice: choice,
        price: 5,
      };
      newBets.push(this.bet);
      localStorage.bets = JSON.stringify(newBets);
      this.getBets();
    },
    formatDate(date) {
      moment.locale('fr');
      const format = 'dddd Do MMMM YYYY, HH:mm';
      if (date) {
        return moment(date).format(format);
      } else {
        return moment(new Date()).format(format);
      }
    },
    isChosen(choice) {
      if (this.bet && this.bet.choice === choice) {
        return 'isChosen';
      } else {
        return '';
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .bet-item {
    margin: 1rem 0;
    border: 1px solid #c7d0d8;
    border-radius: 5px;
    padding: 0.5rem;

    .bet-header {
      color: #c7d0d8;
      font-size: 11px;
    }

    .rating-card {
      background: #ffde59;
      width: 8vw;
      padding: 0.25rem 1rem;
      border-radius: 5px;
      margin: 0 0.5rem;
      &:hover {
        background: #e6c758;
      }

      &.isChosen {
        background: #c7d0d8;
      }

      .rating-team {
        font-size: 11px;
        text-transform: uppercase;
        width: 100%;
        text-align: left;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
      }

      .rating {
        font-weight: bold;
      }
    }

    .bet-link {
      font-size: 12px;

      svg {
        color: gray;
        margin-left: 8px;
        font-size: 14px;
      }
    }
  }
</style>

<template>
  <div class="bet-container">
    <div class="list-games d-flex justify-content-start">
      <button class="btn game-item d-flex align-items-center" v-for="game in games" v-on:click="filterMatchs(game.name)">
        <b-img class="game-logo" :src="game.logo" fluid :alt="game.name"></b-img>
        <span>{{game.name}}</span>
      </button>
    </div>
    <template v-if="matchs.length > 0">
      <bet-item v-for="match in matchs" :match="match"></bet-item>
    </template>
  </div>
</template>

<script>
import BetItem from "../components/BetItem";

export default {
  name: "bet",
  components: {BetItem},
  data: () => {
      return {
        matchs: [],
        chosenGame: 'League of Legends',
        games: [
          {
            name: 'League of Legends',
            logo: 'https://universe.leagueoflegends.com/images/LOL.png'
          },
          {
            name: 'Rocket League',
            logo: 'https://i.redd.it/umv1kgc30to11.png'
          },
          {
            name: 'CS:GO',
            logo: 'https://i.pinimg.com/originals/73/94/eb/7394ebcbd70c48b3e0ff930ce3683da4.png'
          },
          {
            name: 'Overwatch',
            logo: 'https://upload.wikimedia.org/wikipedia/commons/thumb/5/55/Overwatch_circle_logo.svg/1024px-Overwatch_circle_logo.svg.png'
          }
        ]
      }
  },
  beforeMount() {
    this.filterMatchs(this.chosenGame);
  },
  methods: {
    update() {
      if (localStorage.matchs) {
        this.matchs = JSON.parse(localStorage.matchs);
      }
    },
    filterMatchs(chosenGame) {
      this.chosenGame = chosenGame;
      this.update();
      if (this.matchs){
        this.matchs = this.matchs.filter(res => {
          return res.game === this.chosenGame;
        })
      }
      console.log(this.matchs, chosenGame);
    }
  }
}
</script>

<style scoped lang="scss">
  .bet-container {
    padding: 3rem 1rem;

    .list-games {
      .game-item {
        border: 1px solid #c7d0d8;
        border-radius: 50px;
        padding: 4px 10px;
        margin: 0 5px;

        .game-logo {
          height: 20px;
          margin-right: 4px;
        }
      }
    }
  }
</style>

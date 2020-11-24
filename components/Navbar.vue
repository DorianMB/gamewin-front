<template>
  <div>
    <b-navbar>
      <b-navbar-nav>
        <div class="d-flex align-items-center">
          <nuxt-link to="/" class="nav-link">Home</nuxt-link>
          <nuxt-link to="/bet" class="nav-link">Bet</nuxt-link>
          <nuxt-link to="/live" class="nav-link">Live</nuxt-link>
        </div>

        <!-- Navbar dropdowns -->
        <b-nav-item-dropdown id="dropdown-left" right>
          <template #button-content>
            <b-avatar variant="info" class="mr-2" src="https://placekitten.com/300/300"></b-avatar>
            <span>User</span>
          </template>
          <b-dropdown-item href="#">Account</b-dropdown-item>
          <b-dropdown-item href="#">Settings</b-dropdown-item>
          <b-dropdown-item v-on:click="addData()">add data</b-dropdown-item>
          <b-dropdown-item v-on:click="clearData()">clear data</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  methods: {
    addData() {
      localStorage.matchs = JSON.stringify([
        {
          id:1,
          date: new Date(),
          competition: 'compétition 1',
          game: 'League of Legends',
          teams: ['G2', 'SKT'],
          ratings: [21, 10, 1],
          numberOfBets: 45
        },
        {
          id:2,
          date: new Date(),
          competition: 'compétition 1',
          game: 'League of Legends',
          teams: ['G2', 'SKT'],
          ratings: [10, 4, 14],
          numberOfBets: 30
        },
        {
          id:3,
          date: new Date(),
          competition: 'compétition 2',
          game: 'League of Legends',
          teams: ['G2', 'SKT'],
          ratings: [22, 8, 2],
          numberOfBets: 100
        },
        {
          id:4,
          date: new Date(),
          competition: 'RLCS',
          game: 'Rocket League',
          teams: ['Renault Vitality', 'NRG'],
          ratings: [22, 8, 2],
          numberOfBets: 105
        },
      ]);
    },
    clearData() {
      localStorage.clear()
    }
  }
}
</script>

<style scoped lang="scss">
  nav {
    /*background: #c7d0d8;*/
    box-shadow: 0px -2px 20px 0px #c7d0d8;
    .navbar-nav {
      justify-content: space-between;
      width: 100%;
      .nav-link {
        margin: 0 10px;
        &.active {
          color: #ffde59 !important;
        }
      }
      .b-avatar {
        width: 2rem;
        height: 2rem;
      }
    }
  }
</style>

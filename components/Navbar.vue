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
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "Navbar"
}
</script>

<style scoped lang="scss">
  nav {
    /*background: #c7d0d8;*/
    box-shadow: 0px -2px 20px 0px #bababa;
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

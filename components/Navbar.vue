<template>
  <div>
    <b-navbar>
      <b-navbar-nav>
        <div class="d-flex">
          <nuxt-link to="/" class="nav-link">Home</nuxt-link>
          <nuxt-link to="/bet" class="nav-link">Bet</nuxt-link>
          <nuxt-link to="/live" class="nav-link">Live</nuxt-link>
        </div>

        <!-- Navbar dropdowns -->
        <b-nav-item-dropdown id="dropdown-left" text="User" right>
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
    .navbar-nav {
      justify-content: space-between;
      width: 100%;
      .nav-link {
        margin: 0 10px;
        &.active {
          color: #ffde59 !important;
        }
      }
    }
  }
</style>

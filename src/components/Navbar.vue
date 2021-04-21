<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-vue">
    <router-link class="navbar-brand d-flex" :to="{ name: 'Home' }">
      <div class="d-flex flex-column align-items-center text-dark">
        <h2>Gregslist!</h2>
      </div>
    </router-link>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarText"
      aria-controls="navbarText"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon" />
    </button>
    <div class="collapse navbar-collapse text-vue" id="navbarText">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <router-link :to="{ name: 'Home' }" class="nav-link text-dark">
            Home
          </router-link>
        </li>
        <li class="nav-item">
          <router-link :to="{ name: 'About' }" class="nav-link text-dark">
            About
          </router-link>
        </li>
        <li class="nav-item">
          <router-link :to="{ name: 'Cars' }" class="nav-link text-dark">
            Cars
          </router-link>
        </li>
        <li class="nav-item">
          <router-link :to="{ name: 'Houses' }" class="nav-link text-dark">
            Houses
          </router-link>
        </li>
        <li class="nav-item">
          <router-link :to="{ name: 'Jobs' }" class="nav-link text-dark">
            Jobs
          </router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  setup() {
    return {}
  },
  components: {}
}
</script>

<style lang="scss" scoped>

</style>

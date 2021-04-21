<template>
  <header>
    <Navbar />
  </header>
  <!-- NOTE router-view allows the router to determine the component that should be injected -->
  <main>
    <router-view />
    <CreateCarModal />
    <CreateHouseModal />
    <CreateJobModal />
  </main>
  <footer>
    <div class="bg-vue text-dark text-center p-3">
      <h4 class="my-auto">
        Made with <i class="fab fa-vuejs text-vue"></i> by
        Samwise
      </h4>
    </div>
  </footer>
</template>

<script>
import CreateCarModal from './components/CreateCarModal.vue'
import CreateHouseModal from './components/CreateHouseModal.vue'
import CreateJobModal from './components/CreateJobModal.vue'
import Navbar from './components/Navbar'

export default {
  components: {
    Navbar,
    CreateCarModal,
    CreateHouseModal,
    CreateJobModal
  }
}
</script>

<style lang="scss">
@import "./assets/scss/main.scss";
</style>

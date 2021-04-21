<template>
  <div class="houses container">
    <div class="row justify-content-start my-auto">
      <div class="col-1 py-3 text-center">
        <div v-if="state.loading">
          <h2><i class="fab fa-vuejs text-success text-left fa-spin"></i></h2>
        </div>
        <button v-else
                title="Open Create House Form"
                type="button"
                class="btn btn-outline-success"
                data-toggle="modal"
                data-target="#new-house-form"
        >
          <i class="fas fa-plus" aria-hidden="true"></i>
        </button>
      </div>
      <div class="col-3 py-3">
        <h2>Houses</h2>
      </div>
      <div class="row">
        <!-- houses go here v-for house in houses -->
        <House v-for="house in state.houses" :key="house.id" :house="house" />
      </div>
    </div>
  </div>
</template>

<script>
import { computed, onMounted, reactive } from 'vue'
import House from '../components/HouseComponent'
import { housesService } from '../services/HousesService'
import { AppState } from '../AppState'

export default {
  name: 'HousesPage',
  setup() {
    const state = reactive({
      loading: true,
      houses: computed(() => AppState.houses)
    })

    // This fires everytime this component is rendered to the Dom
    // similar to how we were using the 'constructor' of the controllers in MVC
    onMounted(async() => {
      try {
        await housesService.getHouses()
        state.loading = false
      } catch (error) {
        console.error(error)
      }
    })

    return {
      state
    }
  },
  components: {
    House
  }
}
</script>

<style lang="scss" scoped>

</style>

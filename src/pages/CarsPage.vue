<template>
  <div class="cars container">
    <div class="row justify-content-start my-auto">
      <div class="col-1 py-3 text-center">
        <h2 v-if="state.loading">
          <i class="fab fa-vuejs text-success text-left fa-spin"></i>
        </h2>
        <button v-else
                title="Open Create Car Form"
                type="button"
                class="btn btn-outline-success"
                data-toggle="modal"
                data-target="#new-car-form"
        >
          <i class="fas fa-plus" aria-hidden="true"></i>
        </button>
      </div>
      <div class="col-3 py-3">
        <h2>Cars</h2>
      </div>
      <div class="row">
        <!-- cars go here v-for car in cars -->
        <Car v-for="car in state.cars" :key="car.id" :car="car" />
      </div>
    </div>
  </div>
</template>

<script>
import { computed, onMounted, reactive } from 'vue'
import Car from '../components/CarComponent'
import { carsService } from '../services/CarsService'
import { AppState } from '../AppState'

export default {
  name: 'CarsPage',
  setup() {
    const state = reactive({
      loading: true,
      cars: computed(() => AppState.cars)
    })

    // This fires everytime this component is rendered to the Dom
    // similar to how we were using the 'constructor' of the controllers in MVC
    onMounted(async() => {
      try {
        await carsService.getCars()
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
    Car
  }
}
</script>

<style lang="scss" scoped>

</style>

<template>
  <div class="jobs container">
    <div class="jobs container">
      <div class="row justify-content-start my-auto">
        <div class="col-1 py-3 text-center">
          <div v-if="state.loading">
            <h2><i class="fab fa-vuejs text-success text-left fa-spin"></i></h2>
          </div>
          <button v-else
                  title="Open Create Job Form"
                  type="button"
                  class="btn btn-outline-success"
                  data-toggle="modal"
                  data-target="#new-job-form"
          >
            <i class="fas fa-plus" aria-hidden="true"></i>
          </button>
        </div>
        <div class="col-3 py-3">
          <h2>Jobs</h2>
        </div>
      </div>
      <div class="row">
        <!-- jobs go here v-for job in jobs -->
        <Job v-for="job in state.jobs" :key="job.id" :job="job" />
      </div>
    </div>
  </div>
</template>

<script>
import { computed, onMounted, reactive } from 'vue'
import Job from '../components/JobComponent'
import { jobsService } from '../services/JobsService'
import { AppState } from '../AppState'

export default {
  name: 'JobsPage',
  setup() {
    const state = reactive({
      loading: true,
      jobs: computed(() => AppState.jobs)
    })

    // This fires everytime this component is rendered to the Dom
    // similar to how we were using the 'constructor' of the controllers in MVC
    onMounted(async() => {
      try {
        await jobsService.getJobs()
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
    Job
  }
}
</script>

<style lang="scss" scoped>

</style>

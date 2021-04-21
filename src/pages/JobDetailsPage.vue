<template>
  <div class="job-details">
    <h1>Hello From Job Details!</h1>
    <div v-if="state.job">
      JOB DETAILS
      <button type="button" class="btn btn-danger" @click="deleteJob">
        Delete
      </button>
    </div>
  </div>
</template>

<script>
import { useRoute, useRouter } from 'vue-router'
import { AppState } from '../AppState'
import { reactive, computed, onMounted } from 'vue'
import { jobsService } from '../services/JobsService'

export default {
  name: 'JobDetails',
  setup() {
    // ROUTE is the current page info
    const route = useRoute()
    // ROUTER is the toolset of changing routes automatically
    const router = useRouter()
    const state = reactive({
      job: computed(() => AppState.activeJob)
    })

    onMounted(async() => {
      try {
        await jobsService.getJobById(route.params.id)
      } catch (error) {
        console.error(error)
      }
    })

    return {
      route,
      state,
      async deleteJob() {
        try {
          await jobsService.deleteJob(state.job.id)
          // Router is a toolset, here used to change the page after the delete is completed
          // returning the user to the jobs page
          AppState.activeJob = null
          router.push({ name: 'Jobs' })
        } catch (error) {
          console.error(error)
        }
      }
    }
  },
  components: {}
}
</script>

<style lang="scss" scoped>

</style>

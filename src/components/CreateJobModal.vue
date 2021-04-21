<template>
  <div class="modal fade"
       id="new-job-form"
       tabindex="-1"
       role="dialog"
       aria-labelledby="exampleModalLabel"
       aria-hidden="true"
  >
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">
            New Job
          </h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <!-- when submitted run the function provided this can be triggered by the button or the enter key -->
        <form @submit.prevent="createJob">
          <div class="modal-body">
            <!-- Form to create a job  -->
            <div class="form-group">
              <label for="company">Company</label>
              <input type="number"
                     class="form-control"
                     id="company"
                     placeholder="Company..."
                     min="1"
                     v-model="state.newJob.company"
              >
            </div>
            <div class="form-group">
              <label for="title">Title</label>
              <input type="text" class="form-control" id="title" placeholder="Title..." required>
            </div>
            <div class="form-group">
              <label for="hours">Hours</label>
              <input type="number"
                     class="form-control"
                     id="hours"
                     placeholder="Hours..."
                     min="1"
                     max="80"
                     v-model="state.newJob.hours"
              >
            </div>
            <div class="form-group">
              <label for="rate">Rate</label>
              <input type="text"
                     class="form-control"
                     id="rate"
                     placeholder="Rate..."
                     v-model="state.newJob.rate"
                     required
              >
            </div>
            <div class="form-group">
              <label for="description">Description</label>
              <input type="text" class="form-control" id="description" placeholder="Description..." v-model="state.newJob.description">
            </div>
            <div class="form-group">
              <label for="imgUrl">Image Url</label>
              <input type="text" class="form-control" id="imgUrl" placeholder="Image Url..." v-model="state.newJob.imgUrl">
            </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">
              Close
            </button>
            <button type="submit" class="btn btn-primary">
              Create
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive } from 'vue'
import { jobsService } from '../services/JobsService'
import $ from 'jquery'
export default {
  name: 'Component',
  setup() {
    const state = reactive({
      newJob: {}
    })
    return {
      state,
      async createJob() {
        try {
          await jobsService.createJob(state.newJob)
          // NOTE reseting to the empty object resets the input fields
          state.newJob = {}
          // REVIEW CLOSING THE MODAL
          // eslint-disable-next-line no-undef
          $('#new-job-form').modal('hide')
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

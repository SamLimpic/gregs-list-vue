<template>
  <div class="job col-md-4 mb-3">
    <!-- Route parameter getting set with the Params object -->
    <router-link :to="{name: 'JobDetails', params: { id: job.id }}">
      <div class="card shadow">
        <img class="card-img-top img-card p-3" src="https://hungarytoday.hu/wp-content/uploads/2018/02/18ps27.jpg" alt="">
        <div class="card-body">
          <h3 class="card-title">
            <u>
              {{ job.company }} | {{ job.jobTitle }}
            </u>
          </h3>
          <h4>
            <i>${{ job.rate.toFixed(2) }} / Hour</i>
          </h4>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'Job',
  props: {
    job: {
      type: Object,
      required: true
    }
  },
  setup() {
    return {}
  },
  components: {}
}
</script>

<style lang="scss" scoped>

</style>

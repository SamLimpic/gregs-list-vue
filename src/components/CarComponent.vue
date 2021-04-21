<template>
  <div class="car col-md-4 mb-3">
    <!-- Route parameter getting set with the Params object -->
    <router-link :to="{name: 'CarDetails', params: { id: car.id }}">
      <div class="card shadow">
        <img class="card-img-top img-card p-3" :src="car.imgUrl" alt="">
        <div class="card-body">
          <h3 class="card-title">
            <u>
              {{ car.make }} | {{ car.model }}
            </u>
          </h3>
          <h4>
            <i>
              ${{ car.price.toFixed(2) }}
            </i>
          </h4>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'Car',
  props: {
    car: {
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

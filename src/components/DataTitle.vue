<template>
  <div class="text-center">
    <h2 class="text-2xl font-bold text-blue-700">
      <i class="fas fa-globe-americas mr-3"></i>{{ text }}
    </h2>
    <p class="mb-4 text-gray-800">
      {{ timestamp }}
    </p>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'DataTitle',
  props: ['text', 'dataDate'],
  computed: {
    timestamp: function () {
      return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
    },
  },
}
</script>

<template>
  <div class="grid gap-4 justify-center md:grid-cols-3 mt-4">
    <!-- Box 1 -->
    <div
      class="shadow-md bg-white p-10 text-center rounded text-gray-800 max-w-xs"
    >
      <h3 class="text-blue-700 font-bold mb-4 text-xl">
        <i class="fas fa-notes-medical mr-3"></i>Cases
      </h3>
      <div class="container text-left">
        <div class="mb-2">
          <span class="font-bold mr-1">New:</span>
          {{ numberWithCommas(stats.NewConfirmed) }}
        </div>
        <div class="mb-2">
          <span class="font-bold">Total:</span>
          {{ numberWithCommas(stats.TotalConfirmed) }}
        </div>
      </div>
    </div>
    <!-- Box 2 -->
    <div
      class="shadow-md bg-white p-10 text-center text-gray-800 rounded max-w-xs"
    >
      <h3 class="mb-4 font-bold text-xl text-red-700">
        <i class="fas fa-skull-crossbones mr-3"></i>Deaths
      </h3>
      <div class="container text-left">
        <div class="mb-2">
          <span class="font-bold mr-1">New:</span>
          {{ numberWithCommas(stats.NewDeaths) }}
        </div>
        <div class="mb-2">
          <span class="font-bold">Total:</span>
          {{ numberWithCommas(stats.TotalDeaths) }}
        </div>
      </div>
    </div>
    <!-- Box 3 -->
    <div
      class="shadow-md bg-white p-10 text-center text-gray-800 rounded max-w-xs"
    >
      <h3 class="text-green-700 font-bold mb-4 text-xl">
        <i class="fas fa-hospital mr-3"></i>Recovered
      </h3>
      <div class="container text-left">
        <div class="mb-2">
          <span class="font-bold mr-1">New:</span>
          {{ numberWithCommas(stats.NewDeaths) }}
        </div>
        <div class="mb-2">
          <span class="font-bold">Total:</span>
          {{ numberWithCommas(stats.TotalDeaths) }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DataBoxes',
  props: ['stats'],
  methods: {
    numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  },
}
</script>

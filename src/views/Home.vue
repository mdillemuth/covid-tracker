<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />

    <div class="grid justify-center">
      <CountrySelect :countries="countries" @get-country="getCountryData" />
      <button
        @click="clearCountryData"
        v-if="stats.Country"
        class="bg-blue-700 mt-2 text-white rounded p-2 focus:outline-none hover:bg-blue-800"
      >
        Clear Selection
      </button>
    </div>

    <DataBoxes :stats="stats" />

    <!-- button only renders when country is selected  -->
  </main>
  <main
    class="flex flex-col align-center justify-center text-center text-blue-800"
    v-else
  >
    <i class="fas fa-spinner fa-pulse mr-3 text-5xl"></i>
    <span class="mt-2">Fetching data...</span>
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      loading: true,
      title: 'Global Data',
      dataDate: '',
      stats: {},
      countries: [],
    }
  },
  methods: {
    // API request to fetch data
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
    // sets data to selected country
    getCountryData(country) {
      this.stats = country
      this.title = country.Country
    },
    // remove selected country and display global data
    async clearCountryData() {
      this.loading = true
      const data = await this.fetchCovidData()
      this.title = 'Global Data'
      this.stats = data.Global
      this.loading = false
    },
  },
  // initializing state
  async created() {
    const data = await this.fetchCovidData()

    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  },
}
</script>

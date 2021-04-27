<template>
  <select
    @change="onChange()"
    v-model="selected"
    class="form-select block border bg-white p-2 rounded"
  >
    <option value="0">Select Country</option>
    <option v-for="country in countries" :value="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'CountrySelect',
  props: ['countries'],
  data() {
    return {
      selected: 0,
    }
  },
  methods: {
    onChange() {
      const country = this.countries.find((c) => c.ID === this.selected)

      this.$emit('get-country', country)
    },
  },
}
</script>

<template>
    <div class="destination-picker">
        <input autofocus autocomplete="off" placeholder="Add a new country" v-model="search">
        <ul v-if="search">
            <li v-for="country in filteredCountries">
                <a @click.prevent="selectDestination(country)" href="">{{ country.name }}</a>
            </li>
        </ul>
    </div>
</template>

<script>
  import countries from './../assets/countries'

  export default {
    name: 'destination-picker',
    data () {
      return {
        search: ''
      }
    },
    computed: {
      filteredCountries: function () {
        const self = this
        return countries.filter(function (country) {
          return country.name.toLowerCase().indexOf(self.search.toLowerCase()) >= 0
        })
      }
    },
    methods: {
      selectDestination: function (destination) {
        this.$emit('destination-selected', destination)
      }
    }
  }
</script>

<style scoped>

</style>

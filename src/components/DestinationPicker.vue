<template>
    <div class="destination-picker">
        <input autofocus autocomplete="off" placeholder="Add a new country" v-model="search">
        <div v-if="search" class="list-group">
            <a v-for="country in filteredCountries" class="list-group-item" @click.prevent="selectDestination(country)" href="">{{ country.name }}</a>
        </div>
    </div>
</template>

<script>
  import countries from './../assets/countries'

  export default {
    name: 'destination-picker',
    data () {
      return {
        search: '',
        countries: countries
      }
    },
    computed: {
      filteredCountries: function () {
        const self = this
        return self.countries.filter(function (country) {
          return country.name.toLowerCase().indexOf(self.search.toLowerCase()) >= 0
        })
      }
    },
    methods: {
      selectDestination: function (destination) {
        const self = this
        this.$emit('destination-selected', destination)
        self.countries = self.countries.filter((country) => { return destination.name !== country.name })
      }
    }
  }
</script>

<style scoped>
    .destination-picker {
        position: absolute;
        top: 1rem;
        left: 1rem;
        width: 15%;
    }

    input {
        width: 100%;
        padding: 0.6rem;
        border: 1px solid #888;
    }

    .list-group-item {
        font-size: 0.8rem;
        display: block;
        padding: 0.5rem;
        text-decoration: none;
        color: inherit;
        background-color: #fff;
        border: 1px solid #c5c6c6;
        border-bottom: 0;
    }

    .list-group-item:first-child {
        border-top: 0;
    }

    .list-group-item:last-child {
        border: 1px solid #c5c6c6;
    }

    .list-group-item:hover {
        background-color: #c5c6c6;
    }
</style>

<template>
    <div id="app">
        <map-fullscreen :destinations="selectedDestinations"></map-fullscreen>
        <div class="trip-container">
            <h1>My Trip</h1>
            <destination-picker :destinations="unselectedDestinations" v-on:destination-selected="addDestination"></destination-picker>
            <destination-list :destinations="selectedDestinations" v-on:destination-removed="removeDestination"></destination-list>
        </div>
    </div>
</template>

<script>
  import MapFullscreen from './components/MapFullscreen.vue'
  import DestinationPicker from './components/DestinationPicker.vue'
  import DestinationList from './components/DestinationList.vue'

  import countries from './assets/countries'

  export default {
    name: 'app',
    components: {
      MapFullscreen,
      DestinationPicker,
      DestinationList
    },
    data () {
      return {
        selectedDestinations: [],
        unselectedDestinations: countries.sort(name)
      }
    },
    created: function () {
      const savedDestinations = JSON.parse(localStorage.getItem('myDestinations')) || []
      savedDestinations.forEach(this.addDestination)
    },
    watch: {
      selectedDestinations (destinations) {
        localStorage.setItem('myDestinations', JSON.stringify(destinations))
      }
    },
    methods: {
      addDestination: function (destination) {
        this.selectedDestinations.push(destination)
        this.unselectedDestinations = removeDestination(destination, this.unselectedDestinations)
      },
      removeDestination: function (destination) {
        this.unselectedDestinations.push(destination)
        this.unselectedDestinations.sort(name)
        this.selectedDestinations = removeDestination(destination, this.selectedDestinations)
      }
    }
  }

  function removeDestination (destination, array) {
    return array.filter((currentDestination) => { return currentDestination.name !== destination.name })
  }

  function name (a, b) {
    return (a.name > b.name) ? 1 : ((b.name > a.name) ? -1 : 0)
  }
</script>

<style>
    html, body {
        height: 100%;
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: sans-serif;
    }

    *, *:before, *:after {
        box-sizing: inherit;
    }

    #app {
        height: 100%;
    }

    .trip-container {
        position: absolute;
        top: 1rem;
        left: 1rem;
        background-color: #fff;
        padding: 1rem;
        width: 15%;
    }

    h1 {
        font-size: 1rem;
    }
</style>

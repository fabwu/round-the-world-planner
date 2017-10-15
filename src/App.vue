<template>
    <div id="app">
        <map-fullscreen :destinations="selectedDestinations"></map-fullscreen>
        <div class="picker-container">
            <destination-picker :destinations="unselectedDestinations" v-on:destination-selected="addDestination"></destination-picker>
        </div>
        <aside class="sidebar-right">
            <destination-list :destinations="selectedDestinations" v-on:destination-removed="removeDestination"></destination-list>
        </aside>
    </div>
</template>

<script>
  import MapFullscreen from './components/MapFullscreen.vue'
  import DestinationPicker from './components/DestinationPicker.vue'
  import DestinationList from './components/DestinationList.vue'
  import countries from './assets/countries'
  import './assets/icons/ionicons.min.css'

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
        font-size: 13px;
    }

    *, *:before, *:after {
        box-sizing: inherit;
    }

    .hidden {
        display: none;
    }

    #app {
        height: 100%;
    }

    .picker-container {
        position: absolute;
        top: 1rem;
        left: 1rem;
        width: 15%;
    }

    .sidebar-right {
        position: absolute;
        top: 0;
        right: 0;
        width: 15%;
        height: 100%;
        background-color: white;
        box-shadow: 0 2px 2px 0 rgba(0, 0, 0, .14), 0 3px 1px -2px rgba(0, 0, 0, .2), 0 1px 5px 0 rgba(0, 0, 0, .12);
    }
</style>

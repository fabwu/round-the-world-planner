<template>
    <div id="app">
        <map-fullscreen :destinations="destinations"></map-fullscreen>
        <div class="trip-container">
            <h1>My Trip</h1>
            <destination-picker v-on:destination-selected="addDestination"></destination-picker>
            <destination-list :destinations="destinations"></destination-list>
        </div>
    </div>
</template>

<script>
  import MapFullscreen from './components/MapFullscreen.vue'
  import DestinationPicker from './components/DestinationPicker.vue'
  import DestinationList from './components/DestinationList.vue'

  export default {
    name: 'app',
    components: {
      MapFullscreen,
      DestinationPicker,
      DestinationList
    },
    data () {
      return {
        destinations: []
      }
    },
    methods: {
      addDestination: function (destination) {
        this.destinations.push(destination)
      }
    }
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

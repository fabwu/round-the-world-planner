<template>
    <div id="app">
        <map-fullscreen :destinations="destinations"></map-fullscreen>
        <destination-picker v-on:destination-selected="addDestination"></destination-picker>
    </div>
</template>

<script>
  import DestinationPicker from './components/DestinationPicker.vue'
  import MapFullscreen from './components/MapFullscreen.vue'

  export default {
    name: 'app',
    components: {
      MapFullscreen,
      DestinationPicker
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
</style>

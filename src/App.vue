<template>
    <div id="app">
        <map-fullscreen></map-fullscreen>
        <!--<destination-picker v-on:destination-selected="showDestination"></destination-picker>-->
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
    methods: {
      showDestination: function (destination) {
        console.log(destination)
      }
    }
  }
</script>

<style>
    html, body {
        height: 100%;
        margin: 0;
        padding: 0;
    }

    #app {
        height: 100%;
    }
</style>

/* eslint-disable no-undef */
<template>
    <div class="map-fullscreen" id="map">
    </div>
</template>

<script>
  export default {
    name: 'map-fullscreen',
    methods: {
      initMap: function () {
        console.log('t')
      }
    }
  }

  function renderMap () {
    const map = new window.google.maps.Map(document.getElementById('map'), {
      center: {lat: 46.818188, lng: 8.227511999999933},
      zoom: 3
    })
    console.log(map)
//    TODO Style google maps
  }

  window.initMap = renderMap
</script>

<style scoped>
    .map-fullscreen {
        height: 100%;
    }
</style>

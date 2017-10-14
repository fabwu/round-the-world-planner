<template>
    <div class="map-fullscreen" id="map">
    </div>
</template>

<script>
  /* eslint-disable no-undef,no-new */

  let map
  let path
  let markers = []

  export default {
    name: 'map-fullscreen',
    props: ['destinations'],
    watch: {
      destinations (destinations) {
        renderMarkers(destinations)
      }
    }
  }

  function renderMarkers (destinations) {
    markers.forEach((marker) => { marker.setMap(null) })

    markers = destinations.map(function (destination) {
      return new google.maps.Marker({
        position: destination,
        map: map
      })
    })

    if (path) {
      path.setMap(null)
    }

    path = new google.maps.Polyline({path: destinations})
    path.setMap(map)
  }

  function renderMap () {
    map = new window.google.maps.Map(document.getElementById('map'), {
      center: {lat: 46.818188, lng: 8.227511999999933},
      zoom: 3,
      maxZoom: 5,
      minZoom: 3,
      disableDefaultUI: true,
      styles: [
        {
          'featureType': 'administrative',
          'elementType': 'all',
          'stylers': [
            {
              'visibility': 'on'
            },
            {
              'lightness': 33
            }
          ]
        },
        {
          'featureType': 'administrative',
          'elementType': 'label',
          'stylers': [
            {
              'visibility': 'off'
            }
          ]
        },
        {
          'featureType': 'administrative.country',
          'elementType': 'label',
          'stylers': [
            {
              'visibility': 'on'
            }
          ]
        },
        {
          'featureType': 'landscape',
          'elementType': 'all',
          'stylers': [
            {
              'color': '#f2e5d4'
            }
          ]
        },
        {
          'featureType': 'poi.park',
          'elementType': 'geometry',
          'stylers': [
            {
              'color': '#c5dac6'
            }
          ]
        },
        {
          'featureType': 'poi.park',
          'elementType': 'labels',
          'stylers': [
            {
              'visibility': 'on'
            },
            {
              'lightness': 20
            }
          ]
        },
        {
          'featureType': 'road',
          'elementType': 'all',
          'stylers': [
            {
              'lightness': 20
            }
          ]
        },
        {
          'featureType': 'road.highway',
          'elementType': 'geometry',
          'stylers': [
            {
              'color': '#c5c6c6'
            }
          ]
        },
        {
          'featureType': 'road.arterial',
          'elementType': 'geometry',
          'stylers': [
            {
              'color': '#e4d7c6'
            }
          ]
        },
        {
          'featureType': 'road.local',
          'elementType': 'geometry',
          'stylers': [
            {
              'color': '#fbfaf7'
            }
          ]
        },
        {
          'featureType': 'water',
          'elementType': 'all',
          'stylers': [
            {
              'visibility': 'on'
            },
            {
              'color': '#acbcc9'
            }
          ]
        }
      ]
    })
  }

  window.initMap = renderMap
</script>

<style scoped>
    .map-fullscreen {
        height: 100%;
    }
</style>

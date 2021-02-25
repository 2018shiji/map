<template>
  <div id="map" class="container"></div>
</template>

<script>

import 'maptalks/dist/maptalks.css'
import * as maptalks from 'maptalks'
export default {
  name: 'Map',
  mounted () {
    this.$nextTick(() => {
      const map = new maptalks.Map('map', {
        center: [-0.113049, 51.498568],
        zoom: 14,
        baseLayer: new maptalks.TileLayer('base', {
          urlTemplate: 'http://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}.png',
          subdomains: ['a', 'b', 'c', 'd'],
          attribution: '&copy; <a href="http://osm.org">OpenStreetMap</a> contributors, &copy; <a href="https://carto.com/">CARTO</a>'
        })
      })
      console.log('map: ', map)
    })
  }
}
</script>

<style type="text/css">
  html,body{ margin:0px;height:100%;width:100%; }
  .container{ width:100%;height:100% }
</style>

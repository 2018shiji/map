<template>
  <div class="container">
  <div id="map" class="container"></div>
  <div class="pane"><a>Add layer</a><a>Remove Layer</a></div>
  </div>
</template>

<script>


import 'maptalks/dist/maptalks.css'
import * as maptalks from 'maptalks'
export default {
  name: 'App',
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
      var marker = new maptalks.Marker(
        map.getCenter(),
        {
          symbol: {
            textName: 'Layer is added.',
            textWeight: 'bold',
            textSize: 50,
            textFill: '#1bbc9b',
            textHaloFill: '#fff',
            textHaloRadius: 5
          }
        }
      )
      new maptalks.VectorLayer('vector', [marker]).addTo(map)
    })
  }
}
</script>

<style type="text/css">
  .container{ width:100%;height:100% }
  .pane{background:#34495e;line-height:28px;color:#fff;z-index:10;position:absolute;top:20px;right:20px}
</style>

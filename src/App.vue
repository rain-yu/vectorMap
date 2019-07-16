<template>
  <div id="app">
    <div id="jqvmap-world" style="width: 600px; height: 400px; background: #ff0;"></div>
  </div>
</template>

<script>
import $ from './components/jquery'
import 'jqvmap'
import 'jqvmap/dist/maps/jquery.vmap.world.js'
import scrollreveal from 'scrollreveal'

console.log(scrollreveal)
function color (e, t) {
    return "rgba(" + parseInt(e.slice(1, 3), 16) + ", " + parseInt(e.slice(3, 5), 16) + ", " + parseInt(e.slice(5, 7), 16) + ", " + t + ")"
}
export default {
  name: 'app',
  mounted () {
    var sr = new scrollreveal()
        var p = '<svg width="0" height="0"><defs><pattern id="map-pattern" x="0" y="0" width="12" height="12" patternUnits="userSpaceOnUse"><circle cx="3" cy="3" r="3" style="stroke: none; fill: rgba(120,130,140, 0.3)"></circle></pattern></defs></svg>';
    // world map
      $('#jqvmap-world').each(function(){
        $(this).css('visibility', 'hidden');
        $(this).append(p);
        $(this).vectorMap(
            {
              map: 'world_en',
              backgroundColor: 'transparent',
              borderColor: 'transparent',
              borderWidth: 0.25,
              borderOpacity: 0.25,
              color: 'url(#map-pattern)',
              enableZoom: false,
              showTooltip: true,
              selectedColor: null,
              hoverColor: null,
              colors: {
                us: color("#448bff", 0.5),
                ru: color("#14bae4", 0.5),
                gb: "#31c971",
                in: "#f4c414"
              }
            }
        );
        debugger
        sr.reveal(this, {origin:'bottom', distance: '10vh', scale: 0.3, rotate: {x: 65}});
      })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

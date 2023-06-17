<script lang="ts">
  import type { Map } from 'leaflet';
  import * as L from 'leaflet';
  import { getContext } from "svelte";
  import locate from "leaflet.locatecontrol";
  import { layerOpenstreetmap } from "../lib/tileLayers";

  let map: Map = getContext('leafletMap');

  L.control.scale().addTo(map);

  L.control.zoom({
    position: "topright"
  }).addTo(map);
  
  // @ts-ignore
  L.control.locate({
        position: "topright"
  }).addTo(map);



  // TileLayers
  layerOpenstreetmap.addTo(map);

</script>
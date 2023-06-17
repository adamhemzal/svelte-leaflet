<script lang="ts">
  import 'leaflet/dist/leaflet.css';
  import type { Map } from 'leaflet';
  import { map as LMap, DomUtil } from 'leaflet';
  import { setContext, onMount, onDestroy } from "svelte";

  let mapContainer: HTMLDivElement;
	let map: Map;

  export let lat: number = 51.505;
  export let lng: number = -0.09

  map = LMap(DomUtil.create('div'), {
    center: [lat, lng],
    zoom: 11,
    zoomControl: false,
  });
  
  /* 1. OPTION
  map = LMap(DomUtil.create('div')).setView([lat, lng], 13);
  */

  /* 2. OPTION
    map = L.map(L.DomUtil.create('div'), {
        center: [49.2386725171185, 17.62928009033203],
        zoom: 11,
        zoomControl: false,
        //preferCanvas: true,
        layers: [oneLayerGroup, anotherLayourGroup]
    });
  */
  setContext('leafletMap', map);

  onMount(() => {
		mapContainer.appendChild(map.getContainer());
		map.getContainer().style.width = '100%';
		map.getContainer().style.height = '100%';
		map.invalidateSize();
	});

  onDestroy(() => {
    if (map) map.remove();
  });
</script>

<style>
  .map {
    height: 100vh;
    width: 100vw;
  }
</style>

<main>
  <div class='map' bind:this={mapContainer}>
    <slot></slot>
  </div>
</main>
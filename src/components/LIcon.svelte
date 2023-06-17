<script lang="ts">
  import { icon as LIcon } from 'leaflet';

  export let url: string;
  export let size: number = 50;

  let icon = LIcon({
    iconUrl: url,
    iconSize: [size, size],
    popupAnchor: [0, -28],
  });
</script>

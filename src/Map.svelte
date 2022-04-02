<script>
    import { onMount } from 'svelte';
    import { browser } from '$app/env';
    import 'leaflet/dist/leaflet.css';

    export let coords = [50.02777589, 1.31961465];
    export let zoom = 14;
    export let markers = [{
        coords: [50.02777589, 1.31961465],
        label: '<b>Le gîte</b><br>6, rue du Petit Bois<br>Criel-Sur-Mer'
    }];

    let mapElement;


    onMount(async () => {
        if(browser) {
            const leaflet = await import('leaflet');

            const map = leaflet.map(mapElement).setView(coords, zoom);

            leaflet.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
            }).addTo(map);

            for (let marker of markers) {
                leaflet.marker(marker.coords).addTo(map)
                    .bindPopup(marker.label)
                    .openPopup();
            }
        }
    });
</script>
<style>
 .map {
   width: 500px;
   height: 500px;
 }
</style>

<div class="map" bind:this={mapElement}></div>

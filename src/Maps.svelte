<script>
    import { onMount } from 'svelte';
    import { browser } from '$app/env';
    import 'leaflet/dist/leaflet.css';

    onMount(async () => {
        if(browser) {
            const leaflet = await import('leaflet');

            const map = leaflet.map('map').setView([50.02777589, 1.31961465], 14);

            leaflet.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
            }).addTo(map);

            leaflet.marker([50.02777589, 1.31961465]).addTo(map)
                .bindPopup('<b>Le gîte</b><br>6, rue du Petit Bois<br>Criel-Sur-Mer')
                .openPopup();
        }
    });
</script>
<style>
 #map {
   width: 500px;
   height: 500px;
 }
</style>

 <div id="map"></div>

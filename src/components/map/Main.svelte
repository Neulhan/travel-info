<script>
	import Map from "./Map.svelte";
	import MapMarker from "./MapMarker.svelte";
</script>

<Map lat={30} lon={30} zoom={1.3}>
	<MapMarker lat={37.6} lon={127} label="Seoul" />
	<MapMarker lat={35.16} lon={129.04} label="Busan" />
	<MapMarker lat={51.5} lon={-0.129} label="London" />
	<MapMarker lat={40.91} lon={-74.06} label="New york" />
	<MapMarker lat={25.2} lon={55.27} label="Dubai" />
	<MapMarker lat={35.69} lon={139.74} label="Tokyo" />
	<MapMarker lat={34.7} lon={135.5} label="Osaka" />
	<MapMarker lat={13.76} lon={100.5} label="Bangkok" />
	<MapMarker lat={22.3} lon={114.16} label="Hong kong" />
	<MapMarker lat={41.43} lon={2.17} label="Barcelona" />
	<MapMarker lat={12.89} lon={100.9} label="Pattaya" />
	<MapMarker lat={41.9} lon={12.5} label="Rome" />
	<MapMarker lat={40.4} lon={-3.69} label="Madrid" />
	<MapMarker lat={-8.3} lon={115.09} label="Bali" />
	<MapMarker lat={52.52} lon={13.39} label="Berlin" />
	<MapMarker lat={31.22} lon={121.45} label="Shanghai" />
	<MapMarker lat={34.07} lon={-118.26} label="Los Angeles" />
	<MapMarker lat={-33.86} lon={151.1} label="Sydney" />
</Map>

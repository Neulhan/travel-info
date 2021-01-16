<script>
	import Map from './Map.svelte';
    import MapMarker from './MapMarker.svelte';
 
</script>
<Map lat={30} lon={30} zoom={1.3}>
  <MapMarker lat={37.6} lon={127} label="서울"/>
  <MapMarker lat={35.16} lon={129.04} label="부산"/>
  <MapMarker lat={51.5} lon={-0.129} label="런던"/>
  <MapMarker lat={40.91} lon={-74.06} label="뉴욕"/>
  <MapMarker lat={25.2} lon={55.27} label="두바이"/>
  <MapMarker lat={35.69} lon={139.74} label="도쿄"/>
  <MapMarker lat={34.7} lon={135.5} label="오사카"/>
  <MapMarker lat={13.76} lon={100.5} label="방콕"/>
  <MapMarker lat={22.3} lon={114.16} label="홍콩"/>
  <MapMarker lat={41.43} lon={2.17} label="바르셀로나"/>
  <MapMarker lat={12.89} lon={100.9} label="파타야"/>
  <MapMarker lat={41.9} lon={12.5} label="로마"/>
  <MapMarker lat={40.4} lon={-3.69} label="마드리드"/>
  <MapMarker lat={-8.3} lon={115.09} label="발리"/>
  <MapMarker lat={52.52} lon={13.39} label="베를린"/>
  <MapMarker lat={31.22} lon={121.45} label="상하이"/>
  <MapMarker lat={34.07} lon={-118.26} label="로스 엔젤레스"/>
  <MapMarker lat={-33.86} lon={151.1} label="시드니"/>
</Map>
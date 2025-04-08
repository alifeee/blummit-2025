https://docs.mapbox.com/mapbox-gl-js/example/animate-a-line/
https://docs.mapbox.com/mapbox-gl-js/example/animate-marker/
https://docs.mapbox.com/mapbox-gl-js/example/animate-point-along-line/
https://docs.mapbox.com/mapbox-gl-js/example/geojson-polygon/
https://docs.mapbox.com/mapbox-gl-js/example/set-popup/
https://www.mapbox.com/blog/building-cinematic-route-animations-with-mapboxgl

# marker
const marker = new mapboxgl.Marker({color: '#F84C4C'});
marker.setLngLat([52, 1.1]);
marker.addTo(map);

# geojson
map.addSource('line', {'type': 'geojson', 'data': geojson});
map.addLayer({
  'id': 'line-animation', 'type': 'line', 'source': 'line',
  'paint': {'line-color': '#ed6498', 'line-width': 5, 'line-opacity': 0.8}
});
map.getSource('line').setData(geojson);
        
load geojson
get earliest start and latest end time -> update slider
add geojson to map with map.addSource('line', ...)
add layer with map.addLayer('id': 'alfie', ...) to colour line
add callback to slider to:
  get "datetime" from slider fraction (earliest + ratio * (latest - earliest))
  set label to this datetime
  for each geojson layer:
    geojson.features = filter(original_geojson, by_Date)
		update map map.getSource('line').setData(geojson);
		marker.setLngLat([


todo
- add more people (everyone at once)
- trigger animation (splash?) when position updates (to be obvious when zoomed out)
- fade markers based on timestamp age

# Blummit maps

Maps showing routes for Big Blummit 2025.

## export geojson

export geojson from OwnTracks with something like


```bash
for person in alfie clarice evie eli nyama hannah oli sid ; do
  ocat --user "${person}" --device phone --format geojson --from 2025-04-06T00:00 --to 2025-04-07T00:00 | jq '{"'"${person}"'": .}'
done | jq --slurp '. | add' > /var/www/static/owntracks/all.geojson
```

…which puts several `.geojson` files into one JSON file to be loaded.

## MapBox examples

- <https://docs.mapbox.com/mapbox-gl-js/example/animate-a-line/>
- <https://docs.mapbox.com/mapbox-gl-js/example/animate-marker/>
- <https://docs.mapbox.com/mapbox-gl-js/example/animate-point-along-line/>
- <https://docs.mapbox.com/mapbox-gl-js/example/geojson-polygon/>
- <https://docs.mapbox.com/mapbox-gl-js/example/set-popup/>
- <https://www.mapbox.com/blog/building-cinematic-route-animations-with-mapboxgl>

## todo

- add more people (everyone at once)
- trigger animation (splash?) when position updates (to be obvious when zoomed out)
- fade markers based on timestamp age

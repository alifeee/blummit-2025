# Blummit maps

Maps showing routes for Big Blummit 2025.

## export geojson

export geojson from OwnTracks with something like this for each day


```bash
from="2025-04-03"
to="2025-04-04"
day=$(date --date="${from}" '+%A' | tr '[A-Z]' '[a-z]')
for person in alfie clarice evie eli nyama hannah oli sid piotr ; do
  ocat --user "${person}" --device phone --format geojson --from "${from}T00:00" --to "${to}T00:00" | jq '{"'"${person}"'": .}'
done | jq --slurp '. | add' > "/var/www/static/owntracks/all_${from}_${day}.geojson"
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
- add splash loading screen

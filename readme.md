
# Retrieve maps from data sources
``` bash
ogr2ogr \
  -f GeoJSON \
  -where "ADM0_A3 IN ('NLD')" \
  subunits.json \
  ne_10m_admin_0_map_subunits.shp
```

# Retrieve places in country
``` bash
ogr2ogr \
  -f GeoJSON \
  -where "ISO_A2 = 'NL' AND SCALERANK < 30" \
  places_nl.json \
  ne_10m_populated_places.shp
```

# Generate combined feed
``` bash
topojson \
  -o nl.json \
  --id-property SU_A3 \
  --properties name=NAME \
  -- \
  subunits_nl.json \
  places_nl.json
```

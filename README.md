# XYZ Tiles Web Comparer

A website to compare two xyz tile layers

## Usage

Create a config object:

```json
{
  "before": {
    "type": "raster",
    "tiles": ["https://server1.com/tiles-1-path/{z}/{x}/{y}.png"],
    "tileSize": 256
  },
  "after": {
    "type": "raster",
    "tiles": ["https://server2.com/tiles-2-path/{z}/{x}/{y}.png"],
    "tileSize": 256
    // "scheme": "tms"
  },
  "center": [175.52436631107616, -37.65870903235669],
  "zoom": 15
}
```

> The before and after objects must match a source from [the MapLibre style spec](https://maplibre.org/maplibre-style-spec/sources/).

Base64 encode it:

```
ewogICJiZWZvcmUiOiB7CiAgICAidHlwZSI6ICJyYXN0ZXIiLAogICAgInRpbGVzIjogWwogICAgICAiaHR0cHM6Ly9zZXJ2ZXIxLmNvbS90aWxlcy0xLXBhdGgve3p9L3t4fS97eX0ucG5nIgogICAgXSwKICAgICJ0aWxlU2l6ZSI6IDI1NgogIH0sCiAgImFmdGVyIjogewogICAgInR5cGUiOiAicmFzdGVyIiwKICAgICJ0aWxlcyI6IFsiaHR0cHM6Ly9zZXJ2ZXIyLmNvbS90aWxlcy0yLXBhdGgve3p9L3t4fS97eX0ucG5nIl0sCiAgICAidGlsZVNpemUiOiAyNTYsCiAgfSwKICAiY2VudGVyIjogWzE3NS41MjQzNjYzMTEwNzYxNiwgLTM3LjY1ODcwOTAzMjM1NjY5XSwKICAiem9vbSI6IDE1Cn0=
```

Use this as the `config` query parameter value:

```
https://site.com/?config=ewogICJiZWZvcmUiOiB7CiAgICAidHlwZSI6ICJyYXN0ZXIiLAogICAgInRpbGVzIjogWwogICAgICAiaHR0cHM6Ly9zZXJ2ZXIxLmNvbS90aWxlcy0xLXBhdGgve3p9L3t4fS97eX0ucG5nIgogICAgXSwKICAgICJ0aWxlU2l6ZSI6IDI1NgogIH0sCiAgImFmdGVyIjogewogICAgInR5cGUiOiAicmFzdGVyIiwKICAgICJ0aWxlcyI6IFsiaHR0cHM6Ly9zZXJ2ZXIyLmNvbS90aWxlcy0yLXBhdGgve3p9L3t4fS97eX0ucG5nIl0sCiAgICAidGlsZVNpemUiOiAyNTYsCiAgfSwKICAiY2VudGVyIjogWzE3NS41MjQzNjYzMTEwNzYxNiwgLTM3LjY1ODcwOTAzMjM1NjY5XSwKICAiem9vbSI6IDE1Cn0=
```

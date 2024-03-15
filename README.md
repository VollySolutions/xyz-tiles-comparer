# XYZ Tiles Web Comparer

A website to compare two xyz tile layers

## Usage

1. Create a config object

   ```json
   {
     "leftMapStyle": {
       "version": 8,
       "sources": {
         "leftSource": {
           "type": "raster",
           "tiles": ["https://server1.com/tiles-1-path/{z}/{x}/{y}.png"],
           "tileSize": 256
         }
       },
       "layers": [
         {
           "id": "1",
           "type": "raster",
           "source": "leftSource",
           "minzoom": 0,
           "maxzoom": 20
         }
       ]
     },
     "rightMapStyle": {
       "version": 8,
       "sources": {
         "rightSource": {
           "type": "raster",
           "tiles": ["https://server2.com/tiles-2-path/{z}/{x}/{y}.png"],
           "tileSize": 256,
           "scheme": "tms"
         },
         "rightSourceBase": {
           "type": "raster",
           "tiles": ["https://server3.com/tiles-3-path/{z}/{x}/{y}.png"],
           "tileSize": 256
         }
       },
       "layers": [
         {
           "id": "2",
           "type": "raster",
           "source": "rightSourceBase",
           "minzoom": 0,
           "maxzoom": 20
         },
         {
           "id": "1",
           "type": "raster",
           "source": "rightSource",
           "minzoom": 0,
           "maxzoom": 20
         }
       ]
     },
     "center": [175.52436631107616, -37.65870903235669],
     "zoom": 15
   }
   ```

   > The `leftMapStyle` and `rightMapStyle` objects must be a [MapLibre style object](https://maplibre.org/maplibre-style-spec/root/).

2. [Minify the object](https://jsonformatter.org/json-minify) (optional).

3. [Base64 encode it](https://www.base64encode.org/):

   ```
   eyJsZWZ0TWFwU3R5bGUiOnsidmVyc2lvbiI6OCwic291cmNlcyI6eyJsZWZ0U291cmNlIjp7InR5cGUiOiJyYXN0ZXIiLCJ0aWxlcyI6WyJodHRwczovL3NlcnZlcjEuY29tL3RpbGVzLTEtcGF0aC97en0ve3h9L3t5fS5wbmciXSwidGlsZVNpemUiOjI1Nn19LCJsYXllcnMiOlt7ImlkIjoiMSIsInR5cGUiOiJyYXN0ZXIiLCJzb3VyY2UiOiJsZWZ0U291cmNlIiwibWluem9vbSI6MCwibWF4em9vbSI6MjB9XX0sInJpZ2h0TWFwU3R5bGUiOnsidmVyc2lvbiI6OCwic291cmNlcyI6eyJyaWdodFNvdXJjZSI6eyJ0eXBlIjoicmFzdGVyIiwidGlsZXMiOlsiaHR0cHM6Ly9zZXJ2ZXIyLmNvbS90aWxlcy0yLXBhdGgve3p9L3t4fS97eX0ucG5nIl0sInRpbGVTaXplIjoyNTYsInNjaGVtZSI6InRtcyJ9LCJyaWdodFNvdXJjZUJhc2UiOnsidHlwZSI6InJhc3RlciIsInRpbGVzIjpbImh0dHBzOi8vc2VydmVyMy5jb20vdGlsZXMtMy1wYXRoL3t6fS97eH0ve3l9LnBuZyJdLCJ0aWxlU2l6ZSI6MjU2fX0sImxheWVycyI6W3siaWQiOiIyIiwidHlwZSI6InJhc3RlciIsInNvdXJjZSI6InJpZ2h0U291cmNlQmFzZSIsIm1pbnpvb20iOjAsIm1heHpvb20iOjIwfSx7ImlkIjoiMSIsInR5cGUiOiJyYXN0ZXIiLCJzb3VyY2UiOiJyaWdodFNvdXJjZSIsIm1pbnpvb20iOjAsIm1heHpvb20iOjIwfV19LCJjZW50ZXIiOlsxNzUuNTI0MzY2MzExMDc2MTYsLTM3LjY1ODcwOTAzMjM1NjY5XSwiem9vbSI6MTV9
   ```

4. Use this as the `config` query parameter value:

   ```
   https://xyz-tiles-comparer.vollysolutions.com/?config=eyJsZWZ0TWFwU3R5bGUiOnsidmVyc2lvbiI6OCwic291cmNlcyI6eyJsZWZ0U291cmNlIjp7InR5cGUiOiJyYXN0ZXIiLCJ0aWxlcyI6WyJodHRwczovL3NlcnZlcjEuY29tL3RpbGVzLTEtcGF0aC97en0ve3h9L3t5fS5wbmciXSwidGlsZVNpemUiOjI1Nn19LCJsYXllcnMiOlt7ImlkIjoiMSIsInR5cGUiOiJyYXN0ZXIiLCJzb3VyY2UiOiJsZWZ0U291cmNlIiwibWluem9vbSI6MCwibWF4em9vbSI6MjB9XX0sInJpZ2h0TWFwU3R5bGUiOnsidmVyc2lvbiI6OCwic291cmNlcyI6eyJyaWdodFNvdXJjZSI6eyJ0eXBlIjoicmFzdGVyIiwidGlsZXMiOlsiaHR0cHM6Ly9zZXJ2ZXIyLmNvbS90aWxlcy0yLXBhdGgve3p9L3t4fS97eX0ucG5nIl0sInRpbGVTaXplIjoyNTYsInNjaGVtZSI6InRtcyJ9LCJyaWdodFNvdXJjZUJhc2UiOnsidHlwZSI6InJhc3RlciIsInRpbGVzIjpbImh0dHBzOi8vc2VydmVyMy5jb20vdGlsZXMtMy1wYXRoL3t6fS97eH0ve3l9LnBuZyJdLCJ0aWxlU2l6ZSI6MjU2fX0sImxheWVycyI6W3siaWQiOiIyIiwidHlwZSI6InJhc3RlciIsInNvdXJjZSI6InJpZ2h0U291cmNlQmFzZSIsIm1pbnpvb20iOjAsIm1heHpvb20iOjIwfSx7ImlkIjoiMSIsInR5cGUiOiJyYXN0ZXIiLCJzb3VyY2UiOiJyaWdodFNvdXJjZSIsIm1pbnpvb20iOjAsIm1heHpvb20iOjIwfV19LCJjZW50ZXIiOlsxNzUuNTI0MzY2MzExMDc2MTYsLTM3LjY1ODcwOTAzMjM1NjY5XSwiem9vbSI6MTV9
   ```

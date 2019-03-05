# map-sprites

Generates spritesheets that are necessary to display custom icons in the GFW Mapbox GL map, using <a href="https://github.com/mapbox/spritezero">spritezero</a>

## Usage

Install dependencies (`yarn install`). Use the node vesrion declared in package.json as bindings for Mapnik are not available for every node version, then run: 

```
yarn run build
```

This will generate the PNG spritesheet as well as the JSON in `/out`.

The resulting files must be accessible with an absolute URL as described here https://docs.mapbox.com/mapbox-gl-js/style-spec/#root-sprite, and then declared with the `sprite` root property of the GL JSON file, or use the `spritePath` property of the map module.

You will then be able to use icons in layers, for instance:
```
{
  "id": "some-points",
  "type": "symbol",
  "source": "composite",
  "source-layer": "some_points",
  "layout": {
      "icon-image": "port"
  }
}
```


## See also

How to generate glyphs: https://github.com/GlobalFishingWatch/map-glfonts

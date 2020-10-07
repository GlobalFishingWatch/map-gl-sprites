# map-sprites

Generates spritesheets that are necessary to display custom icons in the GFW Mapbox GL map, using <a href="https://github.com/mapbox/spritezero">spritezero</a>

## Usage

Install dependencies (`yarn install`). Use the node version declared in package.json as bindings for Mapnik are not available for every node version, then run:

```
yarn build
```

This will generate the PNG spritesheets as well as the JSONs in `/out`.

The resulting files must be accessible with an absolute URL as described here https://docs.mapbox.com/mapbox-gl-js/style-spec/#root-sprite, and then declared with the `sprite` root property of the GL JSON file.

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

This generates the main spritesheet (`yarn build:main`) as well as the labeler spritesheet (`yarn build:labeler`) thas has SDF sprites (see https://github.com/mapbox/spritezero/pull/66). Demo for labeler icons is available in `/icon`. ⚠️ input SVGs must only use `<path>`s, SDF generation will fail with anything else (`<polygons>`, etc)

## See also

How to generate glyphs: https://github.com/GlobalFishingWatch/map-glfonts

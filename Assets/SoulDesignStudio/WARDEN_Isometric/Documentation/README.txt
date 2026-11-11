WARDEN - Isometric Abandoned Sanatorium Tileset  v1.0
SoulDesignStudio

UNITY
  Scenes/Demo_site and Scenes/Demo_cutaway show the demo built only from these sprites.
  Sprites/HD (64 pixels per unit) and Sprites/Half (32 pixels per unit) are already imported
  with the custom pivot below, so both sets have the same size in the scene.
  Data/ holds the JSON files with the size and pivot of every sprite, and the demo layouts.

CONTENTS (the same sprites are also in the plain PNG download)
  sprites_128/        608 PNG sprites, 1 m grid cell = 128 x 64 px (HD)
  sprites_64/         the same 608 sprites at half size, 1 m grid cell = 64 x 32 px
  sprites_128.json    size and pivot of every sprite (HD set)
  sprites_64.json     size and pivot of every sprite (half-size set)
  previews/           overview sheets and the demo site shown on the store page

  197 assets: 37 wall pieces (tiled, painted, manor, padded and brick walls with doorways,
  double doorways, windows, observation windows, arches and halves), 6 floors, 7 doors (ward, cell,
  swing, wood, double, service, bar gate), 2 staircases, 8 trims, 28 medical pieces (beds, gurneys,
  operating and autopsy tables, morgue wall, cabinets, wheelchairs, IV stand, restraint chair,
  bathroom fixtures), 35 furniture pieces, 21 props, 8 lights, 11 details (signs, vents, bars,
  boards), 6 debris piles and 28 exterior pieces (brick facades, roof, gables, clock tower, portico,
  steps, chimney, fence, gate, lamp posts, dead trees, gravestones, ground and path).

PROJECTION
  2:1 dimetric ("isometric pixel art" projection). One metre of floor is a diamond
  128 px wide and 64 px tall in the HD set (64 x 32 px in the half-size set).
  Modules are 4 m: a 4 x 4 m floor tile is a 512 x 256 px diamond. Walls are 3.5 m tall.
  Every sprite in a set uses the same scale, so everything fits together.
  Transparent background, fixed light from the upper left.

FACINGS
  File names end with the direction the front of the asset faces:
    _S  front towards the lower left of the screen
    _E  front towards the lower right of the screen
    _N  and _W  back views (props only)
  Props come in all four facings. Walls, doors, trims and similar pieces come in _S and _E,
  the two sides a player can see. Floors come in _S and _E (for directional patterns).
  Medical pieces, furniture, stairs, roofs, gables and most exterior pieces come in all four
  facings, like props.
  Upper-floor pieces stack 3.5 m up: move them up by 3.5 * 78.4 px (HD).

PIVOTS AND PLACEMENT
  Each JSON entry gives "pivot_px" [x, y] (pixels from the top-left corner) and
  "pivot_norm" [x, y] (0-1, origin bottom-left, for Unity's custom pivot).
  The pivot is the asset's ground point:
    walls, floors, doors: the left end / corner of the piece on the grid line
    props: the centre of the footprint on the ground
  To place an asset at grid position (x, y) in metres, with x to the east and y to the north:
    screen_x = 64 * (x + y)        (HD set; use 32 for the half-size set)
    screen_y = 32 * (x - y)        (HD set; use 16 for the half-size set)
  then draw the sprite so that its pivot lands on (screen_x, screen_y).
  For things stacked on a surface, move the sprite up by height_m * 78.4 px (HD) or 39.2 px (half size).

DRAW ORDER
  Draw floors first, then everything else from back to front: sort by (x - y) of the
  centre of each asset's footprint, smallest first.

ENGINES
  Godot 4: use Sprite2D nodes with "Centered" off and offset = -pivot_px, or a TileSet
  with texture origin set from the JSON. Turn on Y-sort for the props layer.
  Unity: set Sprite Mode Single, Pivot Custom = pivot_norm, Pixels Per Unit 64 (HD).
  GameMaker / other engines: set the sprite origin to pivot_px.

LICENSE
  See LICENSE.txt.

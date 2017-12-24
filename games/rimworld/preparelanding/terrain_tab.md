Terrain Tab
===========
The terrain tab deals with terrain-related filters.

![Terrain tab](assets/terrain_tab.png)

The list of available filters in this tab is:

- [Biome Type](#biome-type)
- [Terrain Type](#terrain-type)
- [Road Type](#road-type)
- [River Type](#river-type)
- [Movement Times](#movement-times)
    - Current Movement Time
    - Summer Movement Time
    - Winter Movement Time
- [Elevation](#elevation)
- [Time Zone](#time-zone)    
- [Coastal Tiles](#coastal-tiles)
    - Sea coasts
        - Sea coast facing a specific direction
    - Lake coasts
- [Stone Type](#stone-type)
 - [Number of Stones](#number-of-stones)


Biome Type
----------

Choose one of the available biomes (even custom ones from other mods) by clicking the `Select Biome Type` button.

![biome selection](assets/biomes.png)

Once a biome is chosen, only tiles from that biome will be selected.

The vanilla game (as of B18) offers twelves biomes where you can settle (please note that biomes that don't allow bases can't be filtered):
- Arid Shrubland
- Boreal Forest
- Cold Bog (since B18)
- Desert
- Extreme Desert
- Ice Sheet
- Sea Ice
- Temperate Forest
- Temperate Swamp (since B18)
- Tropical Rainforest
- Tropical Swamp (since B18)
- Tundra

Please note that the `Any` biome simply means "All available biomes". 
The `Any` biome is the default filter state, which also means that no specific biome filtering is applied in this state (or put in a different way: all biome tiles match).

Custom biomes from other mods are inherently supported.

Terrain Type
------------

Choose one of the available terrain types (even custom ones from other mods), by clicking the `Select Terrain` button.

![terrain selection](assets/select_terrain.png)

Once a terrain is chosen, only tiles with that terrain will be selected.

The vanilla game offers five terrain types:
- Flat
- Small hills
- Large hills
- Mountainous
- Impassable

Notice that the impassable terrain can't be chosen in `PrepareLanding` as it is not possible to settle your colony in such a terrain.
However the "`Allow impassable tiles`" in the Options tab allow you to choose and filter tiles with an impassable terrain.

Custom terrains from other mods are inherently supported.

Road Type
---------

Choose a combination of the available road types by clicking one or more of the three-state options.

![road selection](assets/select_road.png)

The vanilla game offers five road types (from the smallest to the biggest):
- Dirt path
- Dirt Road
- Stone Road
- Ancient asphalt road
- Ancient asphalt highway

See [three states filtering](filtering.md#three-states) on how to proceed with this type of filter.

The `Reset` button reset all the road filters to their default state (`Partial` state). The `All` button selects all roads (`On` state) while the `None` button deselects all of them (`Off` state).

Custom roads from other mods are inherently supported.

River Type
----------

Choose a combination of the available river types by clicking one or more of the three-state options.

![river selection](assets/select_river.png)

The vanilla game offers four river types (from the biggest to smallest):
- Huge River
- Large River
- River
- Creek

See [three states filtering](filtering.md#three-states) on how to proceed with this type of filter.

The `Reset` button reset all the river filters to their default state (`Partial` state). The `All` button selects all roads (`On` state) while the `None` button deselects all of them (`Off` state).

Custom roads from other mods are inherently supported.

Movement Times
--------------

Movement times filter allows you to filter tiles by the average time it would take to traverse the whole tile (for a pawn with default movement speed), depending on the season.

![movement time selection](assets/select_movement_times.png)

- Current movement time: the time it would take to traverse the tile during the current season.
- Winter movement time: the time it would take to traverse the tile during the winter.
- Summer movement time: the time it would take to traverse the tile during the summer.

Do not forget to click on the `Use filter` if you want the filter to be taken into account.

![movement time selection: click on use](assets/select_movement_times_2.png)

Elevation
---------

Allows to filter tiles by their elevation (in meters). This filter is a [Usable Numeric filter](filtering.md#usable-numeric).

![Elevation filter](assets/select_elevation.png)

Note: technically the vanilla game allows tile elevation to be in the following range: [-500, 5000].

Time Zone
---------

Allows to filter tiles by their time zone on the world map. This filter is a [Usable Numeric filter](filtering.md#usable-numeric).

![Time Zone Filter](assets/select_time_zone.png)

Note that the time zones are in the range [-12, 12].

Coastal Tiles
-------------

A coastal tile is a tile with at least a pool of water (sea or lakes) in an adjacent tile.

The coastal tile filter is a single [three-state filter](filtering.md#orderable-three-states).

![Coastal filter](assets/select_coastal.png)

- `On`: Filter tiles that are only coastal tiles
- `Off`: Filter tiles that are not coastal tiles
- `Partial`: both coastal and not coastal tiles match (default behavior)

There are two kinds of coasts adjacent to a water body that can be filtered in `PrepareLanding`:
- Sea coasts: coasts touching a sea or ocean.
- Lake: coast touching a lake, where a lake is **at most** 15 tiles of water surrounded by land.

It is also possible to filter tiles with a sea coast depending on which direction the coast is facing: North, East, West, South.

![Coastal filter: coast rotation](assets/select_coastal_rotation.png)


Stone Type
----------

Choose a combination of the available stones types by clicking one or more of the three-state options.

![stone selection](assets/select_stone.png)

The vanilla game offers five stone types:
- Granite
- Limestone
- Marble
- Sandstone
- Slate

Stone order is important because the game gives different stones types (by quantity) once in the game map.

You can see the stone order by clicking a tile on the world map and looking at the terrain tab, then searching for the "Stone Type" entry:

![movement time selection](assets/stone_order_terrain_tab.png)

Note that by default, the filtering is ordered. In the above example the precise order is: `Sandstone` then `Limestone` then `Slate`.

You can change the order of the stones in the filter: see the [orderable three states filtering](filtering.md#orderable-three-states) on how to proceed with this type of filter.

If you specifically do **not** want a specific order, click on the `Filter: Ordered` button (which will turn red): this instructs `PrepareLanding` to filter stones without any precise order.

![stone selection: ordered](assets/select_stone_order.png)

![stone selection: no order](assets/select_stone_order2.png)

The `Reset All` button reset all the stone filters to their default state (`Partial` state).

Custom stone types from other mods are inherently supported.


### Number of Stones

You can also use the `number of stones` filter which basically allows you to filter tiles with either 2 or 3 types of stones in it, **whatever these stone types are**.

![number of stones filter](assets/num_of_stones.png)

Notice than when this filter is in use, you can't use the other stone types filter:

![number of stones filter](assets/num_of_stones2.png)



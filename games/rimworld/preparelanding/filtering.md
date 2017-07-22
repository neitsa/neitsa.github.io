# Filtering

There are four types of filter in `PrepareLanding`:

- [Single choice](#single-choice) filters
- [Three state](#three-states) filters
- [Orderable three state](#orderable-three-state) filters
- [Usable numeric](#usable-numeric) filters

## Single Choice

The single choice selection is the simplest one: you only have a single choice to select your filter.

For example, the biome selection is one of them as you can only choose one biome at a time.

![biome selection](assets/biomes.png)

## Three States

Three state items have, as their name implies, three possible states:

- On: ![ON state](assets/on_state.png)
- Off: ![ON state](assets/off_state.png)
- Partial: ![ON state](assets/partial_state.png)

The `On` state means:
    - I absolutely **want** this option when filtering tiles

The `Off` state means:
    - I absolutely **do not want** this option when filtering tiles

The `Partial` state means:
    - I **do not care** if this option is available or not when filtering tiles

Note that when clicking on a state item, the order of appearance is: `Partial` -> `Off` -> `On` -> `Partial` -> etc.


### Three states: simple example

Let's take an example with the [Coastal Tile](terrain.md#coastal-tiles) filter on the [Terrain Tab](terrain.md). (`World Map -> Version: A17b; Seed: flo; World coverage: 5%`)

![coastal filter](assets/select_coastal.png)

Below is an overview of the world map where:

- the Boreal Forest biome is filtered (all Boreal Forest biome tiles are highlighted)
- The coastal tile state is `On`, which means: **coastal tiles must be included**

![Costal Tiles: On state](assets/exemple_three_state1_1.png)

In this state (as we are in the `On` state) all coastal tiles match. Note that this is the same behavior for the `Partial` state (which would mean: I don't care if it's coastal or not).

Now here is an overview of the world map where:

- The Boreal Forest biome is filtered (all Boreal Forest biome tiles are highlighted)
- The coastal tile state is `Off`: **coastal tiles must not be included**

![Costal Tiles: Off state](assets/exemple_three_state1_2.png)

Notice how in this state, coastal tiles were removed from the filtering.

### Three States: advanced example

Here is an example of the [Road Types](terrain.md#road-types) filter on the [Terrain Tab](terrain.md). (`World Map -> Version: A17b; Seed: poker; World coverage: 5%`)

We start with a default filter for road types:

![road filter](assets/select_road.png)

Below is an overview of the world map where:

- The Boreal Temperate Forest biome is filtered (all Temperate Forest biome tiles are highlighted)
- The road filter is its default state (all road filters are in their Partial State which means: **Tiles may or may not have a road.** (this implies that all tiles match).

![road filter: default state](assets/exemple_three_state2_1.png)

Now with the following road filter applied:

![road filter: new filter](assets/exemple_three_state2_3.png)

The above filter means:

- Tiles must have a `Stone Road`
- Tiles may or may not have a `Dirt Path`
- I do not want tiles with a `Dirt Road`, `Ancient Asphalt Road`, `Ancient Asphalt`

Notice the higher priority of the `Stone Road` filter: this immediately makes all tiles with a Stone Road a must have, deselecting all tiles **without** a `Stone Road`.

![road filter: new filter result](assets/exemple_three_state2_2.png)

On the other hand, with the following filter:

![road filter: new filter](assets/exemple_three_state2_4.png)

- Tiles may or may not have a `Dirt Path`
- I do not want tiles with a `Dirt Road`, `Stone Road`, `Ancient Asphalt Road`, `Ancient Asphalt`

Notice how all tiles with or without a `Dirt Path` are selected, but the tiles with the other road types are deselected:

![road filter: new filter result](assets/exemple_three_state2_5.png)

## Orderable Three States

The orderable three state filter works like the [three state filter](#three-states) except the order itself can be changed.

Here is a live example:

![reorderable three state filter](assets/stone_reordering_optimized.gif)

Note that the reordering is only meaningful for the `On` and `Partial` states (the `Off` state, by definition, has no precise order).

The above example means:

- Filter tiles that have `Sandstone` in first position
- Filter tiles that have `Limestone` in second position
- Filter tiles that may or may not have `Slate` in third position
- Do not include tiles that have `Granite`
- Do not include tiles that have `Marble`

As of now, only the `Stone type` filter is reorderable.

## Usable Numeric

A `usable numeric` filter is comprised of three items:

- A on / off button for the filter usage
    - if `on` the filter is taken into account
    - if `off` the filter is not included
- Two numeric fields (int or float) with a min and max value.

Note: integer fields don't let you enter the decimal point while float fields allow you to do so.

![usable numeric filter: example](assets/select_elevation.png)

Do not forget to click on the `Use` button if you want to use the filter!

![usable numeric filter: use](assets/usable_numeric.gif)